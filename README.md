#  TP 9 : Formulaire de Connexion Personnalisé avec Spring Security

##  Objectifs du TP

Ce TP vise à comprendre et personnaliser le mécanisme d'authentification de Spring Security en remplaçant la page de connexion par défaut par un formulaire HTML personnalisé.

### Compétences acquises
-  Configuration complète de Spring Security
-  Création d'un formulaire de login personnalisé
-  Gestion des redirections après authentification
-  Implémentation d'un système de déconnexion sécurisé
-  Gestion des rôles utilisateur (USER/ADMIN)
-  Intégration Thymeleaf avec Spring Security

##  Architecture du Projet

```
TP9-Formulaire-Connexion/
├── src/
│   ├── main/
│   │   ├── java/ma/fstg/security/
│   │   │   ├── config/SecurityConfig.java          # Configuration sécurité
│   │   │   ├── web/AuthController.java             # Contrôleur des vues
│   │   │   └── SecurityApplication.java            # Classe principale
│   │   └── resources/
│   │       ├── templates/                          # Pages HTML
│   │       │   ├── login.html
│   │       │   ├── home.html
│   │       │   ├── admin-dashboard.html
│   │       │   └── user-dashboard.html
│   │       ├── static/css/
│   │       │   └── style.css                       # Styles personnalisés
│   │       └── application.properties              # Configuration Spring
│   └── test/
│       └── resources/
│           └── application.properties              # Configuration tests
├── .mvn/
│   └── jvm.config                                  # Configuration JVM
└── pom.xml                                         # Dépendances Maven
```



##  Comptes de Test

| Rôle | Identifiant | Mot de passe | Accès |
|------|-------------|--------------|-------|
| **ADMIN** | `admin` | `1234` | Toutes les pages |
| **USER** | `user` | `1111` | Pages user et home |


##  Flux d'Authentification

### 1. Accès initial
- Utilisateur accède à `http://localhost:8080`
- Redirection automatique vers `/login`
- Affichage du formulaire personnalisé

### 2. Processus de connexion
- Formulaire POST vers `/authenticate`
- Spring Security valide les credentials
- **Succès** → Redirection vers `/home`
- **Échec** → Retour vers `/login?error=true`

### 3. Navigation après connexion
- **Page d'accueil** (`/home`) : Présentation des espaces accessibles
- **Espace utilisateur** (`/user/dashboard`) : Accessible à USER et ADMIN
- **Espace administrateur** (`/admin/dashboard`) : Réservé aux ADMIN

### 4. Déconnexion
- Formulaire POST vers `/logout`
- Invalidation de la session
- Redirection vers `/login?logout=true`

##  Fonctionnalités de Sécurité Implémentées

###  Authentification
- Formulaire de login personnalisé
- Validation des credentials en mémoire
- Messages d'erreur contextuels

###  Autorisation
- Restrictions par rôles
- Pages publiques vs. pages protégées
- Gestion des accès refusés (403)

###  Session Management
- Déconnexion sécurisée (POST + CSRF)
- Invalidation de session
- Suppression des cookies


##  Points Pédagogiques Clés

### Spring Security Concepts
- **SecurityFilterChain** : Configuration centralisée
- **UserDetailsService** : Gestion des utilisateurs
- **HttpSecurity** : Définition des règles d'accès
- **Authentication Manager** : Processus d'authentification

### Bonnes Pratiques
- Séparation configuration/vues/contrôleurs
- Messages d'erreur utilisateur-friendly
- Protection CSRF systématique
- Vérification des rôles côté serveur ET client

### Intégration Frontend/Backend
- Thymeleaf + Spring Security
- Expressions sécurisées avec `sec:`
- Gestion des états (connecté/déconnecté)
- Redirections conditionnelles



## Démonstration




https://github.com/user-attachments/assets/880dd910-1f66-4e98-8aa2-3f4b4e744bad

## Encadrement & Auteur
**Réalisée par**: BENZIAT hana
<br>
**Encadré par**: Mr.LACHGAR mohammed

