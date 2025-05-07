
# Système de Gestion de Visites Techniques

## 📋 À propos du projet

Le Système de Gestion de Visites Techniques est une plateforme web permettant aux différentes entités (hôpitaux, entreprises, administrations, etc.) de gérer efficacement les rendez-vous de visites techniques. Le système facilite la prise de rendez-vous par les visiteurs et offre un espace administrateur complet pour gérer ces rendez-vous.

### Fonctionnalités principales

- Interface publique pour la prise de rendez-vous
- Espace administrateur sécurisé
- Système de notifications par email
- Gestion complète du cycle de vie des rendez-vous
- Tableaux de bord statistiques
- Interface responsive (desktop, tablette, mobile)

## 🛠️ Technologies utilisées

### Frontend
- **React.js** – Bibliothèque JavaScript pour l'interface utilisateur
- **React Router** – Gestion des routes côté client
- **Axios** – Client HTTP pour les requêtes API
- **Bootstrap** – Framework CSS pour le design responsive
- **Chart.js** – Visualisation des données statistiques

### Backend
- **Node.js** – Environnement d'exécution JavaScript
- **Express.js** – Framework web pour Node.js
- **MySQL** – Système de gestion de base de données relationnelle
- **Sequelize** – ORM pour la gestion de la base de données
- **JWT** – Authentification par token
- **Nodemailer** – Service d'envoi d'emails

### Outils de développement
- **Git** – Gestion de versions
- **ESLint** – Linting du code
- **Jest** – Tests unitaires
- **Docker** – Conteneurisation (optionnel)
- **Concurrently** – Pour exécuter le backend et frontend en une seule commande

## 🏗️ Architecture du projet

```
visite-technique-app/
├── client/                 # Frontend React
│   ├── public/             # Fichiers statiques
│   ├── src/                # Code source React
│   │   ├── components/     # Composants React
│   │   ├── pages/          # Pages de l'application
│   │   ├── services/       # Services (API, etc.)
│   │   ├── utils/          # Fonctions utilitaires
│   │   └── App.js          # Composant principal
│   └── package.json        # Dépendances frontend
│
├── server/                 # Backend Node.js
│   ├── config/             # Configuration
│   ├── controllers/        # Contrôleurs
│   ├── models/             # Modèles Sequelize
│   ├── routes/             # Routes API
│   ├── services/           # Services (email, etc.)
│   ├── utils/              # Fonctions utilitaires
│   ├── app.js              # Application Express
│   └── package.json        # Dépendances backend
│
├── package.json            # Commande principale pour tout lancer
├── .gitignore              # Fichiers ignorés par Git
├── docker-compose.yml      # Configuration Docker (optionnel)
└── README.md               # Ce fichier
```

## 📦 Installation

### Prérequis
- Node.js (v14 ou supérieur)
- MySQL (v5.7 ou supérieur)
- npm ou yarn

### Configuration de la base de données
1. Créez une base de données MySQL :
   ```sql
   CREATE DATABASE visite_technique_db;
   ```

2. Créez un utilisateur avec les droits nécessaires :
   ```sql
   CREATE USER 'visite_user'@'localhost' IDENTIFIED BY 'votre_mot_de_passe';
   GRANT ALL PRIVILEGES ON visite_technique_db.* TO 'visite_user'@'localhost';
   FLUSH PRIVILEGES;
   ```

### Installation des dépendances globales
1. Clonez le dépôt :
   ```bash
   git clone https://github.com/votre-nom/visite-technique-app.git
   cd visite-technique-app
   ```

2. Installez les dépendances globales du projet (client et serveur) :
   ```bash
   npm install
   ```

> ⚠️ Assurez-vous que `concurrently` est bien installé dans le fichier `package.json` principal.

### Fichiers `.env`
Créez deux fichiers `.env` à la racine des dossiers suivants :

#### Backend (`server/.env`)
```
DB_HOST=localhost
DB_USER=visite_user
DB_PASSWORD=votre_mot_de_passe
DB_NAME=visite_technique_db
JWT_SECRET=votre_secret_jwt
EMAIL_USER=votre_email@example.com
EMAIL_PASSWORD=votre_mot_de_passe_email
PORT=5000
```

#### Frontend (`client/.env`)
```
REACT_APP_API_URL=http://localhost:5000/api
```

### Lancer l'application (frontend + backend)
Tu peux maintenant lancer **les deux serveurs** avec une **seule commande** :

```bash
npm run dev
```

> Cette commande utilise `concurrently` pour lancer le backend (`server`) et le frontend (`client`) en parallèle.

Voici à quoi ressemble la commande dans le `package.json` principal :

```json
"scripts": {
  "dev": "concurrently \"npm run server\" \"npm run client\"",
  "server": "cd server && npm run dev",
  "client": "cd client && npm start"
}
```

L'application sera accessible à l'adresse : `http://localhost:3000`

## 🚀 Déploiement

### Production
1. Construisez le frontend :
   ```bash
   cd client
   npm run build
   ```

2. Configurez votre serveur Node.js pour servir les fichiers statiques depuis `client/build`.

### Docker (optionnel)
```bash
docker-compose up -d
```

## 💻 Utilisation

### Interface publique
Les visiteurs peuvent :
- Consulter les informations sur l'entité
- Remplir le formulaire de demande de rendez-vous
- Recevoir des confirmations par email

### Interface administrateur
Les administrateurs peuvent :
- Visualiser les demandes de rendez-vous
- Confirmer, modifier ou rejeter les rendez-vous
- Consulter l'historique des rendez-vous
- Accéder aux statistiques
- Gérer les paramètres du système

## 📊 Structure de la base de données

### Tables principales
- `users` – Administrateurs du système
- `visitors` – Visiteurs demandant des rendez-vous
- `appointments` – Rendez-vous
- `appointment_types` – Types/motifs de rendez-vous
- `notifications` – Historique des notifications envoyées

## 📝 Roadmap

### Phase 1: MVP (Minimum Viable Product)
- [x] Mise en place de l'architecture de base
- [ ] Développement de l'interface publique
- [ ] Système de prise de rendez-vous

### Phase 2: Administration
- [ ] Interface administrateur
- [ ] Gestion des rendez-vous
- [ ] Tableaux de bord

### Phase 3: Notifications
- [ ] Système d'emails automatiques
- [ ] Rappels et confirmations

### Phase 4: Finalisation
- [ ] Tests et corrections
- [ ] Optimisations
- [ ] Documentation utilisateur

## 👥 Contribution

1. Fork le projet
2. Créez votre branche de fonctionnalité (`git checkout -b feature/nouvelle-fonctionnalite`)
3. Committez vos changements (`git commit -m 'Ajout d'une nouvelle fonctionnalité'`)
4. Poussez vers la branche (`git push origin feature/nouvelle-fonctionnalite`)
5. Ouvrez une Pull Request

## 📄 Licence

Ce projet est sous licence [MIT](LICENSE).

## 📞 Contact

Pour toute question ou suggestion concernant ce projet, veuillez contacter :
- Email : votre-email@example.com
- GitHub : [votre-nom](https://github.com/votre-nom)
