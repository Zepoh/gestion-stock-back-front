# 📦 Système de Gestion de Stock

## 🎯 **Vue d'ensemble**

Système complet de gestion de stock développé avec une architecture moderne **Spring Boot + React TypeScript**. Cette application permet la gestion complète des articles, clients, fournisseurs, commandes et mouvements de stock avec un système de permissions granulaire basé sur les rôles utilisateur.

## 🏗️ **Architecture du Projet**

```
gestion-stock/
├── 🔧 gestion-de-stock-api/     # Backend Spring Boot (Port 8080)
│   ├── src/main/java/com/bouali/gestiondestock/
│   │   ├── 🎮 controller/       # Contrôleurs REST (24 fichiers)
│   │   ├── 📊 dto/              # Data Transfer Objects (18 fichiers)
│   │   ├── 🗄️ model/            # Entités JPA (20 fichiers)
│   │   ├── 🔧 services/         # Services métier (30 fichiers)
│   │   ├── 🗃️ repository/       # Repositories JPA (14 fichiers)
│   │   ├── ✅ validator/        # Validateurs (12 fichiers)
│   │   ├── ⚙️ config/           # Configuration Spring (4 fichiers)
│   │   ├── 🚨 exception/        # Gestion des erreurs (4 fichiers)
│   │   └── 🛠️ utils/            # Utilitaires (2 fichiers)
│   └── src/main/resources/
│       ├── application.yml      # Configuration principale
│       └── data.sql            # Données d'initialisation
├── ⚛️ gestion-stock-react/      # Frontend React TypeScript (Port 3000)
│   ├── src/
│   │   ├── 📱 components/       # Composants réutilisables (18 fichiers)
│   │   ├── 📄 pages/            # Pages de l'application (37 fichiers)
│   │   ├── 🔧 services/         # Services API (13 fichiers)
│   │   ├── 🗂️ store/            # Redux Store (11 fichiers)
│   │   ├── 🎣 hooks/            # Hooks personnalisés (3 fichiers)
│   │   ├── 🔧 utils/            # Utilitaires (1 fichier)
│   │   └── 📝 types/            # Types TypeScript (1 fichier)
│   └── public/                  # Assets statiques
└── 📚 README.md                 # Documentation complète
```

### **🔧 Backend - Spring Boot API**
- **Framework** : Spring Boot 3.4.5
- **Java** : Version 21
- **Base de données** : PostgreSQL 42.7.5
- **Sécurité** : Spring Security 6.4.5 + JWT
- **ORM** : Spring Data JPA 3.4.5
- **Documentation API** : Swagger/OpenAPI 3.0
- **Stockage photos** : Intégration Flickr API
- **Build** : Maven 3.8+
- **Tests** : JUnit 5 + Mockito

### **⚛️ Frontend - React TypeScript**
- **Framework** : React 18.2.0 + TypeScript 4.9.5
- **UI Library** : Material-UI (MUI) 5.14.20
- **State Management** : Redux Toolkit 1.9.7
- **Routing** : React Router v6.20.1
- **HTTP Client** : Axios 1.6.2 avec intercepteurs JWT
- **Data Grid** : MUI X DataGrid 6.18.2
- **Build** : Create React App 5.0.1
- **Tests** : Jest + React Testing Library

## 🚀 **Fonctionnalités Principales**

### **📊 Gestion des Données**
- ✅ **Articles** : CRUD complet, catégories, photos, historiques
- ✅ **Clients & Fournisseurs** : Gestion complète avec adresses
- ✅ **Commandes** : Commandes clients et fournisseurs
- ✅ **Mouvements de Stock** : Entrées, sorties, corrections
- ✅ **Catégories** : Organisation des articles

### **👥 Gestion des Utilisateurs**
- ✅ **Authentification** : JWT avec refresh tokens
- ✅ **Inscription d'entreprise** : Processus complet
- ✅ **Système de rôles** : USER, MANAGER, ADMIN
- ✅ **Permissions granulaires** : Accès contrôlé par rôle

### **📱 Interface Utilisateur**
- ✅ **Dashboard** : Statistiques en temps réel
- ✅ **Design responsive** : Compatible mobile/desktop
- ✅ **Navigation intuitive** : Sidebar adaptée aux permissions
- ✅ **Gestion des photos** : Upload et affichage automatique

## 🔐 **Système de Permissions**

### **🔵 USER (Utilisateur)**
- Tableau de bord (lecture)
- Articles (consultation uniquement)
- Profil personnel

### **🟡 MANAGER (Gestionnaire)**
- Toutes les permissions USER +
- Articles (CRUD complet)
- Clients & Fournisseurs (CRUD)
- Commandes et mouvements de stock
- Catégories

### **🔴 ADMIN (Administrateur)**
- Toutes les permissions MANAGER +
- Gestion des utilisateurs
- Paramètres système
- Gestion des entreprises

## 🛠️ **Technologies Utilisées**

### **Backend**
| Technologie | Version | Usage |
|-------------|---------|-------|
| Spring Boot | 3.4.5 | Framework principal |
| Spring Security | 6.4.5 | Authentification/Autorisation |
| Spring Data JPA | 3.4.5 | ORM et accès données |
| PostgreSQL | 42.7.5 | Base de données |
| JWT | - | Tokens d'authentification |
| Swagger | 3.0 | Documentation API |
| Lombok | - | Réduction du code boilerplate |
| Flickr API | - | Stockage des images |

### **Frontend**
| Technologie | Version | Usage |
|-------------|---------|-------|
| React | 18.2.0 | Framework UI |
| TypeScript | 4.9.5 | Typage statique |
| Material-UI | 5.14.20 | Composants UI |
| Redux Toolkit | 1.9.7 | Gestion d'état |
| React Router | 6.20.1 | Navigation |
| Axios | 1.6.2 | Client HTTP |
| MUI DataGrid | 6.18.2 | Tableaux avancés |

## 📋 **Prérequis**

### **Environnement de développement**
- ☕ **Java 21** ou supérieur
- 🐘 **PostgreSQL 12** ou supérieur
- 🟢 **Node.js 18** ou supérieur
- 📦 **npm** ou **yarn**
- 🔧 **Maven 3.8** ou supérieur

### **Comptes externes**
- 📸 **Compte Flickr** (pour le stockage des images)

## ⚡ **Installation Rapide**

### **1. Cloner le projet**
```bash
git clone <repository-url>
cd gestion-stock
```

### **2. Configuration de la base de données**
```sql
-- Créer la base de données PostgreSQL
CREATE DATABASE gestiondestock;
CREATE USER gestionuser WITH PASSWORD 'password';
GRANT ALL PRIVILEGES ON DATABASE gestiondestock TO gestionuser;
```

### **3. Configuration du backend**
```bash
cd gestion-de-stock-api

# Configurer application.yml
cp src/main/resources/application.yml.example src/main/resources/application.yml
# Éditer les paramètres de base de données et Flickr

# Installer et démarrer
mvn clean install
mvn spring-boot:run
```

### **4. Configuration du frontend**
```bash
cd gestion-stock-react

# Installer les dépendances
npm install

# Démarrer en mode développement
npm start
```

### **5. Accès à l'application**
- 🌐 **Frontend** : http://localhost:3000
- 🔧 **Backend API** : http://localhost:8080
- 📚 **Documentation API** : http://localhost:8080/swagger-ui.html

## 📚 **Documentation Détaillée**

- 📖 [**Guide d'Installation Complet**](docs/INSTALLATION.md)
- 🏗️ [**Architecture Technique**](docs/ARCHITECTURE.md)
- 🔌 [**Documentation API**](docs/API.md)
- 🗄️ [**Schéma de Base de Données**](docs/DATABASE.md)
- 👥 [**Guide Utilisateur**](docs/USER_GUIDE.md)
- 🚀 [**Guide de Déploiement**](docs/DEPLOYMENT.md)
- 🔧 [**Configuration Avancée**](docs/CONFIGURATION.md)

## 🧪 **Tests**

### **Backend**
```bash
cd gestion-de-stock-api
mvn test
```

### **Frontend**
```bash
cd gestion-stock-react
npm test
```

## 🚀 **Déploiement**

### **Production avec Docker**
```bash
# Construire les images
docker-compose build

# Démarrer les services
docker-compose up -d
```

### **Variables d'environnement**
```env
# Base de données
DB_HOST=localhost
DB_PORT=5432
DB_NAME=gestiondestock
DB_USER=gestionuser
DB_PASSWORD=password

# JWT
JWT_SECRET=your-secret-key
JWT_EXPIRATION=86400000

# Flickr
FLICKR_API_KEY=your-flickr-api-key
FLICKR_API_SECRET=your-flickr-secret
```

## 🤝 **Contribution**

1. **Fork** le projet
2. **Créer** une branche feature (`git checkout -b feature/AmazingFeature`)
3. **Commit** les changements (`git commit -m 'Add AmazingFeature'`)
4. **Push** vers la branche (`git push origin feature/AmazingFeature`)
5. **Ouvrir** une Pull Request

## 📄 **Licence**

Ce projet est sous licence MIT. Voir le fichier [LICENSE](LICENSE) pour plus de détails.

## 👨‍💻 **Auteurs**

- **Vladimir Nzali** - *Développeur Principal* - [GitHub](https://github.com/vladimir-nzali)

## 🙏 **Remerciements**

- Spring Boot Team pour l'excellent framework
- React Team pour la bibliothèque UI
- Material-UI pour les composants élégants
- Communauté open source pour les outils utilisés

## 📞 **Support**

Pour toute question ou problème :
- 📧 **Email** : support@gestionstock.com
- 🐛 **Issues** : [GitHub Issues](https://github.com/vladimir-nzali/gestion-stock/issues)
- 📚 **Documentation** : [Wiki du projet](https://github.com/vladimir-nzali/gestion-stock/wiki)

---

**⭐ N'hésitez pas à donner une étoile si ce projet vous a été utile !**
