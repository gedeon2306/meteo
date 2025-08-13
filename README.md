# 🌤️ Application Météo Vue.js

Une application météo moderne et responsive construite avec Vue.js 3, TypeScript et Vite. L'application permet de rechercher la météo d'une ville et affiche automatiquement une image de fond correspondante.

## ✨ Fonctionnalités

- 🔍 Recherche de météo par ville
- 🌡️ Affichage de la température en degrés Celsius
- 💨 Informations sur le vent et l'humidité
- 🌤️ Description des conditions météorologiques
- 🖼️ Images de fond dynamiques basées sur la ville recherchée
- 📱 Interface responsive et moderne
- ⚡ Chargement rapide avec Vite
- 🔄 Gestion d'erreurs et états de chargement

## 🛠️ Technologies utilisées

- **Vue.js 3** - Framework JavaScript progressif
- **TypeScript** - Typage statique pour JavaScript
- **Vite** - Outil de build rapide
- **Axios** - Client HTTP pour les requêtes API
- **Remixicon** - Icônes modernes
- **CSS3** - Styles avec effets de transparence et animations

## 📋 Prérequis

- Node.js (version 16 ou supérieure)
- npm ou yarn

## 🚀 Installation

1. **Cloner le repository**
   ```bash
   git clone <url-du-repo>
   cd meteo
   ```

2. **Installer les dépendances**
   ```bash
   npm install
   ```

3. **Configuration des variables d'environnement**
   
   Copiez le fichier d'exemple :
   ```bash
   cp .env.example .env
   ```
   
   Éditez le fichier `.env` et ajoutez vos clés API :
   ```env
   VITE_WEATHER_API_KEY=votre_cle_api_openweathermap_ici
   VITE_PIXABAY_API_KEY=votre_cle_api_pixabay_ici
   ```

4. **Obtenir les clés API**

   - **OpenWeatherMap API** : Inscrivez-vous sur [openweathermap.org](https://openweathermap.org/api) pour obtenir une clé gratuite
   - **Pixabay API** : Inscrivez-vous sur [pixabay.com/api/docs](https://pixabay.com/api/docs/) pour obtenir une clé gratuite

5. **Lancer l'application en mode développement**
   ```bash
   npm run dev
   ```

6. **Ouvrir l'application**
   
   L'application sera disponible à l'adresse : `http://localhost:5173`

## 📁 Structure du projet

```
meteo/
├── public/                 # Fichiers statiques
├── src/
│   ├── assets/            # Ressources (images, icônes)
│   │   └── vue.svg
│   ├── components/        # Composants Vue (vide pour l'instant)
│   ├── App.vue           # Composant principal de l'application
│   ├── main.ts           # Point d'entrée de l'application
│   ├── style.css         # Styles globaux
│   └── vite-env.d.ts     # Types pour Vite
├── .env                   # Variables d'environnement (non commité)
├── .env.example          # Exemple de configuration
├── .gitignore            # Fichiers à ignorer par Git
├── index.html            # Page HTML principale
├── package.json          # Dépendances et scripts
├── tsconfig.json         # Configuration TypeScript
├── vite.config.ts        # Configuration Vite
└── README.md             # Documentation du projet
```

## 🔧 Scripts disponibles

- `npm run dev` - Lance le serveur de développement
- `npm run build` - Compile l'application pour la production
- `npm run preview` - Prévisualise la version de production

## 🌐 APIs utilisées

### OpenWeatherMap API
- **Endpoint** : `https://api.openweathermap.org/data/2.5/weather`
- **Fonction** : Récupération des données météorologiques
- **Paramètres** : ville, clé API, unités (métriques)

### Pixabay API
- **Endpoint** : `https://pixabay.com/api/`
- **Fonction** : Récupération d'images de fond
- **Paramètres** : clé API, requête (nom de la ville), type d'image

## 🎨 Fonctionnalités de l'interface

### Design moderne
- Interface avec effet de verre (glassmorphism)
- Arrière-plan dynamique basé sur la ville recherchée
- Animations fluides et transitions
- Icônes Remixicon pour une meilleure UX

### Responsive
- Adaptation automatique aux différentes tailles d'écran
- Interface optimisée pour mobile et desktop

### États de l'interface
- **État initial** : Message d'accueil
- **Chargement** : Spinner animé
- **Succès** : Affichage des données météo
- **Erreur** : Messages d'erreur explicites

## 🔒 Sécurité

- Les clés API sont stockées dans des variables d'environnement
- Le fichier `.env` est exclu du contrôle de version
- Utilisation du préfixe `VITE_` pour exposer les variables côté client

## 🚀 Déploiement

### Build pour la production
```bash
npm run build
```

### Prévisualisation du build
```bash
npm run preview
```

Les fichiers de production seront générés dans le dossier `dist/`.

## 🤝 Contribution

1. Fork le projet
2. Créez une branche pour votre fonctionnalité (`git checkout -b feature/AmazingFeature`)
3. Committez vos changements (`git commit -m 'Add some AmazingFeature'`)
4. Push vers la branche (`git push origin feature/AmazingFeature`)
5. Ouvrez une Pull Request

## 📝 Licence

Ce projet est sous licence MIT. Voir le fichier `LICENSE` pour plus de détails.

## 🆘 Support

Si vous rencontrez des problèmes ou avez des questions :

1. Vérifiez que toutes les dépendances sont installées
2. Assurez-vous que vos clés API sont correctement configurées
3. Consultez la documentation des APIs utilisées
4. Ouvrez une issue sur GitHub

---

**Développé avec ❤️ en Vue.js 3**
