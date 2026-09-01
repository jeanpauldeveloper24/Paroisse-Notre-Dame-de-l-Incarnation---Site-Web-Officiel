# paroisse-Notre-Dame-de-L-Incarnation

![Status](https://img.shields.io/badge/Status-Development-blue)
![Docker](https://img.shields.io/badge/Docker-MySQL-2496ED?logo=docker&logoColor=white)
![Deploy](https://img.shields.io/badge/Render-Deployment-46E3B7?logo=render&logoColor=white)

Bienvenue sur le dépôt officiel du site web de la **Paroisse Notre-Dame de l'Incarnation**. Ce document récapitule la présentation du projet, les choix techniques, la structure architecturale ainsi que les droits de propriété et la licence logicielle.

---

## 📖 Présentation

Le projet du site web officiel de la Paroisse Notre-Dame de l'Incarnation a pour objectif d'offrir une plateforme moderne, rapide, accessible et permanente à l'ensemble de la communauté paroissiale et aux visiteurs. 

Il permet d'assurer une communication fluide concernant :
- Les horaires des messes dominicales et en semaine.
- Les annonces et actualités paroissiales.
- L'organisation des mouvements, chorales et groupes de prière.
- Les démarches et guides pratiques pour les sacrements (Baptême, Mariage, Confirmation, etc.).
- Les demandes d'intentions de messe et la prise de contact avec le secrétariat presbytéral.

---

## 🛠 Technologies

Le projet s'appuie sur une combinaison de technologies modernes pour garantir performance, résilience et simplicité de maintenance :

| Composant | Technologie Choisie | Rôle |
| :--- | :--- | :--- |
| **Framework & Front** | Laravel 13 + Blade + Tailwind CSS | Architecture monolithique solide et rendu serveur rapide. |
| **Authentification** | Laravel Breeze | Espace d'administration sécurisé pour l'équipe presbytérale. |
| **Base de Données** | MySQL 8.0 (via Docker) | Stockage relationnel structuré des données. |
| **Gestion DB Local** | Adminer (Docker) | Interface d'administration DB ultra-léger. |
| **Cache & Performance** | CDN Edge (Cloudflare) + Service Worker (PWA) | Distribution sous 10 ms et prise en charge du mode hors-ligne.|
---

## 🏗 Architecture

Le système est conçu sur la base d'un **découplage strict entre le rendu et les données** afin de garantir une disponibilité maximale :

```text
                     +---------------------------+
                     |     Utilisateur / Client  |
                     +-------------+-------------+
                                   |
                         (Requêtes HTTP/HTTPS)
                                   v
                     +---------------------------+
                     |    CDN Edge / Cache static |
                     +-------------+-------------+
                                   |
                  +----------------+----------------+
                  |                                 |
                  v                                 v
   [ Pages Statiques / Assets ]             [ API Dynamique ]
   (Horaires, Info, Sacrements)             (Render / Backend)
                                                    |
                                                    v
                                            [ Base MySQL ]
                                            (Docker / Cloud)

Environnement de Développement Isolé : Utilisation de Docker Compose localement pour orchestrer l'instance MySQL et les services associés sans polluer la machine hôte.

Déploiement Automatisé (CI/CD) : Chaque mise à jour poussée sur la branche principale (main) déclenche automatiquement un build et un redéploiement sur Render.

Optimisation des Performances : Distribution des pages statiques via des nœuds CDN pour minimiser la latence mondiale.

🎨 Charte Graphique Officielle (NDI)

- **Bleu Ciel Marial (`#72C7FF`) :** Couleur dominante d'arrière-plan & identité visuelle.
- **Bleu Nuit (`#1B2449`) :** Navigation, pieds de page et typographies fortes.
- **Or / Jaune Sacré (`#FFD700`) :** Boutons d'action, alertes et éléments de mise en valeur.
- **Police Titres :** `Cinzel` / `Playfair Display` (Serif).
- **Police Texte :** `Inter` (Sans-Serif).

📜 Licence & Propriété
Propriété du Produit Final & du Code Source
Propriétaire du Produit Final : L'intégralité du produit fini (l'application déployée, les médias, les contenus, le nom de domaine, l'image officielle et la marque) est la propriété exclusive et inaliénable de la Paroisse Notre-Dame de l'Incarnation.

Propriétaire du Code Source : L'ensemble du code source, des scripts, des configurations d'infrastructure et des bases de données développés dans le cadre de ce projet est cédé et appartient exclusivement à la Paroisse Notre-Dame de l'Incarnation.

Collaborateurs du Projet
Le développement et l'architecture du projet sont assurés par les deux collaborateurs suivants :

kouassi yao jean paul danick, developpeur multimédia



© 2026 Paroisse Notre-Dame de l'Incarnation - Tous droits réservés.
