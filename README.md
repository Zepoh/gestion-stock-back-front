# 📦 Système de Gestion de Stock

## 🎯 Description du Projet

Application complète de gestion de stock développée avec **Spring Boot** (backend) et **React TypeScript** (frontend). Cette solution permet de gérer efficacement les articles, clients, fournisseurs, commandes et mouvements de stock avec un système de permissions basé sur les rôles.

## 🏗️ Architecture

```
📁 gestion-stock/
├── 🔧 gestion-de-stock-api/     # Backend Spring Boot (Port 8080)
└── ⚛️ gestion-stock-react/      # Frontend React (Port 3000)
```

### Backend - Spring Boot
- **Framework** : Spring Boot 3.4.5
- **Java** : Version 21
- **Base de données** : PostgreSQL
- **Sécurité** : JWT + Spring Security
- **Documentation** : Swagger/OpenAPI

### Frontend - React
- **Framework** : React 18.2.0 + TypeScript
- **UI** : Material-UI (MUI)
- **État** : Redux Toolkit
- **Navigation** : React Router v6

## ✨ Fonctionnalités Principales

### 📊 Gestion des Données
- ✅ **Articles** : Création, modification, suppression avec photos
- ✅ **Catégories** : Organisation des articles
- ✅ **Clients & Fournisseurs** : Gestion complète avec adresses
- ✅ **Commandes** : Suivi des commandes clients et fournisseurs
- ✅ **Stock** : Mouvements d'entrée, sortie et corrections

### 👥 Gestion des Utilisateurs
- ✅ **Authentification** : Connexion sécurisée avec JWT
- ✅ **Inscription** : Création d'entreprise avec premier admin
- ✅ **Rôles** : USER, MANAGER, ADMIN avec permissions différentes
- ✅ **Profils** : Gestion des informations personnelles

### 📱 Interface
- ✅ **Dashboard** : Statistiques et vue d'ensemble
- ✅ **Design responsive** : Compatible mobile et desktop
- ✅ **Navigation intuitive** : Menu adapté selon les permissions

## 🔐 Système de Permissions

| Rôle | Permissions |
|------|-------------|
| **USER** | Consultation du tableau de bord et des articles |
| **MANAGER** | + Gestion articles, clients, fournisseurs, stock |
| **ADMIN** | + Gestion utilisateurs et paramètres système |

## 🚀 Guide de Démarrage Rapide

### 📋 Prérequis

Avant de commencer, assurez-vous d'avoir installé :

- ☕ **Java 21** ou supérieur
- 🐘 **PostgreSQL 12** ou supérieur  
- 🟢 **Node.js 18** ou supérieur
- 📦 **npm** ou **yarn**
- 🔧 **Maven 3.8** ou supérieur

### 🗄️ Étape 1 : Configuration de la Base de Données

1. **Démarrer PostgreSQL** et créer la base de données :

```sql
-- Se connecter à PostgreSQL
psql -U postgres

-- Créer la base de données
CREATE DATABASE gestock;

-- Créer un utilisateur (optionnel)
CREATE USER gestion_user WITH PASSWORD 'votre_mot_de_passe';
GRANT ALL PRIVILEGES ON DATABASE gestock TO gestion_user;
```

### 🔧 Étape 2 : Configuration du Backend

1. **Naviguer vers le dossier backend** :
```bash
cd gestion-de-stock-api
```

2. **Configurer la base de données** dans `src/main/resources/application.yml` :
```yaml
spring:
  datasource:
    url: jdbc:postgresql://localhost:5432/gestock
    username: postgres
    password: votre_mot_de_passe
    driver-class-name: org.postgresql.Driver
```

3. **Configurer Flickr** (pour les photos) dans le même fichier :
```yaml
flickr:
  apiKey: votre_flickr_api_key
  apiSecret: votre_flickr_api_secret
  appKey: votre_flickr_app_key
  appSecret: votre_flickr_app_secret
```

4. **Installer et démarrer le backend** :
```bash
# Installer les dépendances
mvn clean install

# Démarrer l'application
mvn spring-boot:run
```

Le backend sera accessible sur : **http://localhost:8080**

### ⚛️ Étape 3 : Configuration du Frontend

1. **Ouvrir un nouveau terminal** et naviguer vers le dossier frontend :
```bash
cd gestion-stock-react
```

2. **Installer les dépendances** :
```bash
npm install
```

3. **Démarrer l'application React** :
```bash
npm start
```

Le frontend sera accessible sur : **http://localhost:3000**

### 🎉 Étape 4 : Premier Démarrage

1. **Ouvrir votre navigateur** et aller sur http://localhost:3000

2. **Créer votre première entreprise** :
   - Cliquer sur "S'inscrire"
   - Remplir les informations de l'entreprise
   - Un compte administrateur sera créé automatiquement

3. **Se connecter** avec les identifiants créés

4. **Explorer l'application** :
   - Dashboard pour voir les statistiques
   - Articles pour gérer les produits
   - Clients/Fournisseurs pour les contacts
   - Utilisateurs pour gérer l'équipe (admin seulement)

## 📚 URLs Importantes

Une fois l'application démarrée :

- 🌐 **Application principale** : http://localhost:3000
- 🔧 **API Backend** : http://localhost:8080
- 📖 **Documentation API** : http://localhost:8080/swagger-ui.html
- 🔍 **Actuator** : http://localhost:8080/actuator/health

## 🛠️ Commandes Utiles

### Backend
```bash
# Compiler sans tests
mvn clean compile

# Exécuter les tests
mvn test

# Créer le JAR
mvn clean package

# Démarrer en mode debug
mvn spring-boot:run -Dspring-boot.run.jvmArguments="-Xdebug -Xrunjdwp:transport=dt_socket,server=y,suspend=n,address=5005"
```

### Frontend
```bash
# Démarrer en mode développement
npm start

# Créer le build de production
npm run build

# Exécuter les tests
npm test

# Analyser le bundle
npm run build && npx serve -s build
```

## 🔧 Configuration Avancée

### Variables d'Environnement

Créer un fichier `.env` dans le dossier frontend :
```env
REACT_APP_API_URL=http://localhost:8080
REACT_APP_VERSION=1.0.0
```

### Profils Spring Boot

Pour différents environnements, créer des fichiers :
- `application-dev.yml` (développement)
- `application-prod.yml` (production)

Démarrer avec un profil spécifique :
```bash
mvn spring-boot:run -Dspring-boot.run.profiles=dev
```

## 🐛 Résolution de Problèmes

### Problèmes Courants

1. **Erreur de connexion à la base de données** :
   - Vérifier que PostgreSQL est démarré
   - Vérifier les paramètres de connexion dans `application.yml`

2. **Port déjà utilisé** :
   - Backend : Changer le port dans `application.yml` (`server.port: 8081`)
   - Frontend : Utiliser `PORT=3001 npm start`

3. **Erreur CORS** :
   - Vérifier la configuration CORS dans `SecurityConfiguration.java`

4. **Photos ne s'affichent pas** :
   - Vérifier la configuration Flickr
   - Créer un compte Flickr et obtenir les clés API

### Logs Utiles

```bash
# Voir les logs du backend
tail -f logs/application.log

# Logs détaillés Spring Boot
mvn spring-boot:run -Dlogging.level.com.bouali.gestiondestock=DEBUG
```

## 📞 Support

Pour toute question ou problème :
- 📧 Créer une issue sur le repository
- 📚 Consulter la documentation Swagger
- 🔍 Vérifier les logs d'application

## 🎯 Prochaines Étapes

Après l'installation réussie :

1. **Personnaliser** les paramètres de l'entreprise
2. **Créer** les premières catégories d'articles
3. **Ajouter** des articles avec photos
4. **Inviter** des utilisateurs avec différents rôles
5. **Explorer** toutes les fonctionnalités disponibles

---

**🎉 Félicitations ! Votre système de gestion de stock est maintenant opérationnel !**
