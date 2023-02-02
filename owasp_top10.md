# OWASP Top 10 2022

- [OWASP Top 10 2022](#owasp-top-10-2022)
  - [Broken Access Control](#broken-access-control)
    - [Exemples](#exemples)
    - [Solutions](#solutions)
  - [Cryptographic Failures](#cryptographic-failures)
    - [Exemples](#exemples-1)
    - [Solutions](#solutions-1)
  - [Injection](#injection)
    - [Exemples](#exemples-2)
    - [Solutions](#solutions-2)
  - [Insecure Design](#insecure-design)
    - [Exemples](#exemples-3)
    - [Solutions](#solutions-3)
  - [Security Misconfiguration](#security-misconfiguration)
    - [Exemples](#exemples-4)
    - [Solutions](#solutions-4)
  - [Vulnerable and Outdated Components](#vulnerable-and-outdated-components)
    - [Exemples](#exemples-5)
    - [Solutions](#solutions-5)
  - [Identification and Authentication Failures](#identification-and-authentication-failures)
    - [Exemples](#exemples-6)
    - [Solutions](#solutions-6)
  - [Software and Data Integrity Failures](#software-and-data-integrity-failures)
    - [Exemples](#exemples-7)
    - [Solutions](#solutions-7)
  - [Security Logging and Monitoring Failures](#security-logging-and-monitoring-failures)
    - [Exemples](#exemples-8)
    - [Solutions](#solutions-8)
  - [Server-Side Request Forgery](#server-side-request-forgery)
    - [Exemples](#exemples-9)
    - [Solutions](#solutions-9)

## Broken Access Control

> Mauvaise gestion des droits d'accès

### Exemples

- Violation du principe de moindre privilège ou de refus par défaut, où l'accès ne doit être autorisé que pour des capacités, des rôles ou des utilisateurs particuliers, mais est disponible pour tout le monde.
- Contournement des contrôles d'accès en modifiant l'URL (tampon de paramètre ou navigation forcée), l'état interne de l'application ou la page HTML, ou en utilisant un outil d'attaque modifiant les requêtes API.
- Accès à l'API avec des contrôles d'accès manquants pour POST, PUT et DELETE.
- Élévation de privilège. Agir en tant qu'utilisateur sans être connecté ou agir en tant qu'administrateur lors de la connexion en tant qu'utilisateur.
- Manipulation de métadonnées, telles que la relecture ou la modification d'un jeton de contrôle d'accès JSON Web Token (JWT), ou d'un cookie ou d'un champ caché manipulé pour élever les privilèges ou abuser de l'invalidation du JWT.
- Navigation forcée vers des pages authentifiées en tant qu'utilisateur non authentifié ou vers des pages privilégiées en tant qu'utilisateur standard.

### Solutions

- Séparation des privilèges
- Whitelist des URL, des paramètres, ...
- Deny by default
- Log les accès et les tentatives d'accès
- Rate limit

## Cryptographic Failures

> Utilisation de chiffrement faible, non sécurisé, ou mauvaise utilisation de chiffrement

### Exemples

md5, pas de salt, ...

### Solutions

- Utiliser des algorithmes de chiffrement forts
- Saler les mots de passe (unique par utilisateur) et autres données sensibles

## Injection

> Possibilité d'injecter du code à un endroit non désiré
>
### Exemples

Injection SQL, [XSS](web_vulnerabitities.md#cross-site-scripting-xss), XML, ...

### Solutions

Vérifier les entrées utilisateurs, utiliser des API sécurisées, ...

## Insecure Design

> Architecture et conception d'un systeme qui, même bien implémenté, est vulnérable à cause de son architecture ou de sa conception.

### Exemples

- Utilisation de la fonctionnalité de téléchargement de fichiers sans contrôle d'accès.
- Utilisation de récupération de mot de passe par question secrète sans contrôle d'accès.

### Solutions

- Mettre en place des contrôles d'accès
- Appliquer les principes de sécurité

## Security Misconfiguration

> Mauvaise configuration des composants, des paramètres, des identifiants et des mots de passe

### Exemples

- Utilisation de mots de passe par défaut.
- Utilisation de mots de passe non sécurisés.
- Pas d'hardening du serveur.
- Unnecessary services enabled.
- Error messages contenant des informations sensibles.

### Solutions

- Configurer correctement les mots de passe
- Configurer correctement les services
- Hardening du serveur
- Limiter au strict nécessaire les services
- Ne pas afficher les messages d'erreurs

## Vulnerable and Outdated Components

> Utilisation de composants obsolètes ou vulnérables

### Exemples

- Utilisation de librairies obsolètes.
- Utilisation de librairies avec des vulnérabilités connues.

### Solutions

- Connaitre les librairies utilisées
- Mettre à jour les librairies
- Vérifier les vulnérabilités connues sur les librairies utilisées

## Identification and Authentication Failures

> Mauvaise gestion de l'identification et de l'authentification

### Exemples

- Possibilité de s'inscrire avec un nom d'utilisateur déjà existant.
- Possibilité de brute force sur les mots de passe.
- Mauvaise gestion de la recupération de mot de passe.
- Non utilisation de 2FA.
- Exposition de l'id de session dans l'URL.

### Solutions

- Limiter le nombre de tentatives de connexion
- Limiter le nombre de tentatives de récupération de mot de passe
- Implémenter l'authentification multi-facteurs
- Ne pas utiliser les mots de passe par défaut
- Vérifier la complexité des mots de passe
- Générer des id de session aléatoires (coté serveur)

## Software and Data Integrity Failures

> Mauvaise gestion de l'intégrité du programme

### Exemples

- Plugins malveillants.
- CI/CD mal sécurisé.

### Solutions

- Limiter les parties tierces
- Vérifier les plugins
- Signer les plugins ou les applications
- Processus de relecture du code

## Security Logging and Monitoring Failures

> Ne pas avoir pouvoir détecter et retracer les attaques et les erreurs

### Exemples

- Pas de logs
- Logs non sécurisés
- Logs non centralisés localement
- Pas d'alertes

### Solutions

- Mettre en place des logs pour tous les contrôles d'accès
- DevSecOps team doit être impliqué dans la mise en place des logs
- Etablir des plans de réponse aux incidents

## Server-Side Request Forgery

> Possibilité de forcer le serveur à effectuer des requêtes non désirées

### Exemples

- Non vérification de l'url renseignée par l'utilisateur

### Solutions

- Firewall: whitelist des urls autorisées
- Vérifier les données renseignées par l'utilisateur
- Désactiver les requêtes HTTP
