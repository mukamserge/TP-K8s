# Plan de démo

## Analyse des besoins backend pour une application Wordpress
- **Base de données SQL**: Wordpress utilise une base de données SQL pour stocker les articles, les utilisateurs, les configurations, etc.
- **Serveur de cache**: Utilisation d'un serveur de cache comme Memcached pour améliorer les performances en réduisant la charge sur la base de données.

## Étape 1: Définir les Custom Resource Definitions (CRD) nécessaires
- CRD pour le Vcluster x Wordpress
- CRD pour la base de données
- CRD pour le cache

## Étape 2: Créer des compositions Crossplane
- Composition pour Vcluster qui encapsule la ressource Wordpress, configure l'application et la relie à la base de données et au cache
- Composition pour la base de données qui prévoit le déploiement et la configuration propre au Wordpress
- Composition pour le cache qui met en place une instance Memcached

## Étape 2.1: Définir les objets Kubernetes nécessaires pour utiliser les compositions
- Environnement Vcluster Wordpress en utilisant la composition correspondante
- Base donnée SQL spécifique a Wordpress en utilisant la composition correspondante
- Base de Cache spécifique a Wordpress en utilisant la composition dédiée

## Étape 3: Publier les CRD et les compositions sur un dépôt GitHub
- Utiliser Git pour versionner et partager les configurations

## Étape 4: Utiliser ArgoCD pour déployer les compositions sur un cluster Kubernetes
- Configurer ArgoCD pour surveiller le dépôt GitHub
- Définir les Applications ArgoCD pour l'ensemble des CRDs et Compositions
- Définir les Applications ArgoCD pour le déploiement de l'application Wordpress et de ses backends
- Observer le déploiement et la gestion des ressources via ArgoCD et Kubectl

## Étape 5: Vérification et tests
- Vérifier que le Vcluster est opérationnel
- Tester le déploiement de Wordpress, accéder à l'interface et publier un article
- Confirmer que la base de données et le cache fonctionnent correctement avec Wordpress - check BDD
