<script setup lang="ts">
  import { ref } from 'vue'
  import axios from 'axios'
  const api_key_weather = ref("a36e8d6df1dc639763c67499234631c9")
  const api_key_image = ref("50127580-f8d33a9d65ba89083b3745706")
  const ville = ref('')
  const url = ref('')
  const url_image = ref('')
  const dataweather = ref([])
  const dataimage = ref([])
  const loading = ref(false)
  const error = ref(null)
  const nb = ref(null)

  const updateBodyBackground = (imageUrl) => {
    if (imageUrl) {
      document.body.style.backgroundImage = `url(${imageUrl})`
    }
  }

  const fetchWeather = async () => {
    
    nb.value = Math.floor(Math.random() * 5)
    loading.value = true
    error.value = null
    dataimage.value =[]
    if (ville.value) {
      url.value = `https://api.openweathermap.org/data/2.5/weather?q=${ville.value}&appid=${api_key_weather.value}&units=metric`
      try {
        const response = await axios.get(url.value)
        dataweather.value = await response.data
        // console.log(dataweather.value)
      } catch (err) {
        // console.error("Erreur lors de la récupération des données météo:", err)
        if (err.response && err.response.status === 404) {
          error.value = "Ville non trouvée. Veuillez vérifier le nom de la ville."
        } else {
          error.value = "Erreur de connexion ou de récupération des données."
        }
      } finally {
        loading.value = false
      }

      url_image.value = `https://pixabay.com/api/?key=${api_key_image.value}&q=${ville.value}&image_type=photo&pretty=true`
      try {
        const responseImage = await axios.get(url_image.value)
        dataimage.value = await responseImage.data
        if (dataimage.value.hits && dataimage.value.hits.length > 0) {
          updateBodyBackground(dataimage.value.hits[nb.value].webformatURL)
        }
      } catch (errdataimage) {
        console.error("Erreur lors de la récupération de l'image:", errdataimage)
      }
    } else {
      loading.value = false
      error.value = "Veuillez entrer une ville"
      updateBodyBackground('https://static1.mclcm.net/iod/images/v2/69/photo/394723/1280x720_80_300_000000x10x0.jpg?ts=20230228124113')
    }
  }
</script>

<template>
  <div class="card">
    <div class="search-container">
        <input v-model="ville" type="text" class="search-input" placeholder="Entrez une ville">
        <button @click="fetchWeather()" class="search-button"><i class="ri-search-2-line"></i></button>
    </div>
    <div v-if="dataweather.length !== 0 && !loading && !error" class="weather-info">
        <h2>{{ dataweather.name }}, {{ dataweather.sys.country }}</h2>
        <p><i class="ri-temp-cold-line weather-icon"></i> Température: {{ dataweather.main.temp }}°C</p>
        <p><i class="ri-sun-fill weather-icon"></i> Condition: {{ dataweather.weather[0].description }}</p>
        <p><i class="ri-water-percent-fill weather-icon"></i> Humidité: {{ dataweather.main.humidity }}%</p>
        <p><i class="ri-windy-line weather-icon"></i> Vent: {{ dataweather.wind.speed }} km/h</p>
    </div>
    <div v-else-if="loading" class="weather-info">
        <div class="loader"></div>
    </div> 
    <div v-else-if="error" class="weather-info">
      <h2 v-if="error" class="error-message">{{ error }}</h2>
    </div>
    <div v-else class="weather-info">
      <h2 >Entrez une ville.</h2>
    </div>
    <div v-if="dataimage.hits && dataimage.hits.length > 0" class="image-container">
      <!-- <img :src="dataimage.hits[`${nb}`].webformatURL" width="200" height="200" alt="Image de la ville" class="city-image"> -->
    </div>
  </div>
</template>

<style scoped>
</style>
