# Rapport Technique du Projet QuiZine

-----

# Introduction

Le projet **QuiZine** est une initiative innovante qui combine l'interactivité des **quiz** avec l'univers de la **cuisine**. Conçu dans un cadre académique avec des contraintes de temps strictes, ce projet illustre notre capacité à développer une application web complète en utilisant des technologies modernes.

QuiZine offre aux utilisateurs la possibilité de créer, partager et participer à des quiz thématiques, en mettant l'accent sur la cuisine, tout en étant ouverte à d'autres sujets. L'application intègre des fonctionnalités sociales, permettant aux utilisateurs d'interagir, de commenter et d'évaluer les quiz, favorisant ainsi une expérience communautaire riche.

Ce rapport technique détaille la structure de l'équipe, les objectifs du projet, l'architecture technique, le modèle de données, les défis rencontrés et les leçons apprises.

-----

# Organisation de l'Équipe

## Structure et Responsabilités

L'équipe de développement de QuiZine a adopté une approche collaborative avec une répartition claire des responsabilités :

  * **Frontend** : Développement de l'interface utilisateur, des composants interactifs et de l'expérience utilisateur. (Mariem CHEIKH ROUHOU, Ola HNEINI, Mathieu WAHARTE)
  * **Backend** : Conception de l'API REST, implémentation des services métiers et sécurisation des données. (Antonin RUSSAC, Raphaël THIEFFRY, Emma DEGOT)
  * **Base de données** : Modélisation des données, optimisation des requêtes et mise en place de l'ORM. (Antonin RUSSAC, Raphaël THIEFFRY, Emma DEGOT)
  * **Infrastructure** : Configuration du déploiement, automatisation et gestion de l'environnement. (Ethan PUYAUBREAU)

Cette structure a permis un travail parallèle efficace tout en maintenant la cohérence du système grâce à des interfaces bien définies.

## Méthodologie de Travail

Le projet a suivi une méthodologie inspirée des principes **Agile**, adaptée à sa courte durée :

  * **Réunions quotidiennes** : Points d'avancement réguliers pour la synchronisation.
  * **Carnet de bord** : Documentation continue des décisions et solutions.
  * **Diagramme de Gantt** : Planification et suivi temporel des tâches.
  * **Utilisation de GitHub** : Gestion des *issues*, *pull requests* et revues de code.
  * **Communication continue** : Canaux de communication dédiés pour une résolution rapide des problèmes.

-----

# Objectifs du Projet

Les objectifs de QuiZine ont été définis dès le début pour guider le développement et établir des critères de réussite clairs.

## Objectifs Fonctionnels

  * Création d'une application de quiz interactive et ludique.
  * Implémentation d'une interface utilisateur intuitive et *responsive*.
  * Développement de fonctionnalités sociales (amis, commentaires, évaluations).
  * Mise en place d'un système de classement et de statistiques.
  * Gestion des utilisateurs avec différents niveaux d'accès.

## Objectifs Techniques

  * Utilisation de technologies web modernes et performantes.
  * Mise en œuvre d'une architecture **scalable** et maintenable.
  * Conception d'une base de données relationnelle optimisée.
  * Implémentation de pratiques de développement collaboratif.
  * Déploiement d'une solution sécurisée et accessible en ligne.

## Contraintes

  * Développement dans un délai très court (4-5 jours).
  * Nécessité d'une collaboration efficace entre plusieurs développeurs.
  * Intégration de plusieurs technologies et *frameworks*.
  * Respect des bonnes pratiques de développement.

-----

# Architecture Technique

L'architecture de QuiZine a été pensée pour être modulaire, évolutive et facile à maintenir, s'articulant autour de composants distincts qui communiquent via des interfaces bien définies.

## Frontend

Le **frontend** de QuiZine est développé avec des technologies modernes pour une expérience utilisateur fluide :

| Technologies Frontend | Description |
| --------------------- | -------------- |
| **Framework** | Angular 17 |
| **Langage** | TypeScript |
| **CSS** | TailwindCSS |
| **Tests** | Jest |
| **Gestion d'état** | NGRX Store |

L'interface a été conçue selon une approche "**mobile-first**", avec des maquettes initiales réalisées sur Figma pour valider le design.

Les fonctionnalités avancées du frontend incluent :

  * Un système de **composants modulaires** et réutilisables.
  * Une gestion d'état centralisée avec **NGRX**.
  * Un système de *routing* pour une navigation fluide.
  * Des formulaires réactifs avec validation côté client.
  * Des animations pour améliorer l'expérience utilisateur.

### Explication Détaillée du Frontend

Le frontend de QuiZine vise à offrir une interface utilisateur interactive et conviviale, permettant aux utilisateurs de :

  * **Découvrir et participer à des quiz** ( `ExploreComponent`, `QuizCardComponent`).
  * **Créer et gérer leurs propres quiz** (`CreateQuizComponent`, `EditQuizComponent`).
  * **Consulter leur historique de quiz et leurs scores** (`ProfileComponent`, `QuizScoreComponent`, `QuizRecapComponent`).
  * **Interagir avec d'autres utilisateurs** (fonctionnalité d'amis potentielle dans `ProfileComponent`).
  * **Gérer leur profil utilisateur** (`ProfileComponent`).
  * **S'authentifier et s'inscrire** (`LandingComponent`, `LoginComponent`, `RegisterComponent`).

Les technologies clés sont :

  * **Angular** : Framework principal pour l'interface utilisateur, avec Angular CLI.
  * **TypeScript** : Langage de programmation pour le développement Angular, offrant un typage statique.
  * **HTML** et **CSS** (probablement avec Tailwind CSS) pour la structure et le style.
  * **Modules Angular** : `CommonModule` et `FormsModule`.
  * **Composants Angular** : L'application est modulaire, avec des composants réutilisables.
  * **Services Angular** : `APIService` (communication backend) et `QuizService` (logique métier).
  * **RxJS** : Bibliothèque de programmation réactive pour gérer les flux de données asynchrones.
  * **État global** : `AppStore` (informations utilisateur, historique) et `gameSessionStore` (état de la session de jeu).
  * **Gestion des routes** : `RouterModule`.

Les techniques et méthodes employées sont :

  * **Architecture basée sur les composants** pour faciliter la maintenance et l'évolutivité.
  * **Gestion de l'état centralisée** via des *stores* pour le partage des données et la prévisibilité.
  * **Programmation réactive** avec RxJS pour gérer les interactions et les réponses du backend.
  * **Data Binding** pour la synchronisation des données.
  * **Validation de formulaires** via `FormsModule`.
  * **Déploiement avec Docker** pour une conteneurisation aisée.

Le choix d'Angular et TypeScript est motivé par leur capacité à gérer des applications web complexes avec une bonne maintenabilité et performance. L'architecture par composants et RxJS favorisent la réutilisation du code et une gestion efficace des opérations asynchrones.

Les composants sont créés avec `@Component`, les services avec `@Injectable`. Le **Data Binding** (`{{ quiz.nom }}`) et la liaison d'événements (`(click)="startQuiz()"`) sont largement utilisés. La navigation est gérée par le service `Router`. L'état de l'application est géré par les *stores* `AppStore` et `gameSessionStore` via des `BehaviorSubject`.

En résumé, le frontend de QuiZine est une application Angular bien structurée, utilisant des technologies et techniques modernes pour une expérience utilisateur riche et interactive, favorisant la maintenabilité et l'évolutivité.

-----

## Backend

Le **backend** de QuiZine est conçu pour être robuste, performant et sécurisé :

| Technologies Backend | Description |
| ---------------------- | --------------------------- |
| **Framework** | ExpressJS |
| **Langage** | TypeScript |
| **Base de données** | PostgreSQL (via Supabase) |
| **Authentication** | JWT + Passport |
| **Documentation API** | Swagger/OpenAPI |

L'architecture backend suit les principes **REST** pour la conception de l'API, avec une séparation claire des responsabilités :

  * **Couche de routage** pour la gestion des requêtes HTTP.
  * **Couche de contrôleurs** pour l'implémentation de la logique métier.
  * **Couche de services** pour l'interaction avec les données.
  * **Middleware** pour l'authentification, la validation et la gestion des erreurs.

Cet arrangement facilite la maintenance et l'évolutivité du code.

### Explication Détaillée du Backend

Le backend de QuiZine est une API Node.js qui gère les quiz, les utilisateurs, les sessions de jeu et d'autres fonctionnalités. Ses objectifs principaux sont :

  * **Gestion des utilisateurs** : Authentification, inscription et gestion des profils.
  * **Gestion des quiz** : Création, modification, suppression et recherche de quiz.
  * **Gestion des sessions de jeu** : Création, participation et suivi des scores.
  * **Interaction en temps réel** : Permettre aux utilisateurs de jouer ensemble en temps réel.
  * **API RESTful** : Fournir une API claire et documentée.

Les technologies utilisées sont :

  * **Node.js** : Environnement d'exécution JavaScript côté serveur.
  * **Express** : Framework web pour Node.js.
  * **Supabase** : Backend as a Service (BaaS) basé sur PostgreSQL (`https://supabase-quiz.kerboul.me`).
  * **Passport** : Middleware d'authentification pour Node.js (authentification locale).
  * **bcrypt** : Bibliothèque de hachage de mots de passe.
  * **Socket.IO** : Bibliothèque pour la communication en temps réel.
  * **Swagger** : Outil de documentation d'API.
  * **k6** : Outil de test de charge.

Les techniques et méthodes employées comprennent :

  * **Architecture RESTful** pour une communication standardisée.
  * **Middleware** pour l'authentification (`middleware/passport.ts`), les sessions et la sécurité.
  * **Gestion des erreurs** centralisée.
  * **Validation des données** pour prévenir les erreurs et failles.
  * **Hachage des mots de passe** avec bcrypt.
  * **Communication en temps réel** avec Socket.IO (`sockets/gameSocket.ts`).
  * **Documentation API** automatique avec Swagger (`swagger.ts`).
  * **Tests de charge** avec k6 (`k6_api_smoke.test.js`).

Les choix technologiques sont motivés par la simplicité, la performance et l'écosystème étendu de Node.js et Express. Supabase simplifie la gestion de la base de données et de l'authentification. Passport, bcrypt, Socket.IO, Swagger et k6 sont essentiels pour la sécurité, les fonctionnalités en temps réel, la documentation et l'assurance qualité.

La mise en œuvre implique :

1.  **Configuration de Supabase** : Connexion via le client Supabase (`supabaseClient.ts`).
2.  **Routes et contrôleurs** : Définition des routes dans `routes/index.ts` et logique métier dans les contrôleurs.
3.  **Modèles** : Définition des modèles de données dans le dossier `models` et interaction avec la base de données via le client Supabase.
4.  **Authentification** : Utilisation de Passport et bcrypt.
5.  **Sessions de jeu** : Création et gestion dans `sessionController.ts`, avec Socket.IO pour la communication en temps réel (`sockets/gameSocket.ts`).
6.  **Documentation API** : Configuration de Swagger dans `swagger.ts` et `swaggerOptions.js`, avec documentation via JSDoc.
7.  **Tests de charge** : Configuration des tests k6 dans `k6_api_smoke.test.js`.

En résumé, le backend de QuiZine est une API Node.js bien structurée, utilisant des technologies modernes pour gérer les quiz, les utilisateurs et les sessions de jeu.

-----

## Infrastructure et Déploiement

L'infrastructure de déploiement de QuiZine utilise des technologies modernes de conteneurisation et d'intégration continue :

```
Client <--HTTPS--> Reverse Proxy <--> Frontend Container
                                    <--> Backend Container <--> Supabase (PostgreSQL)
```

L'automatisation du déploiement repose sur :

  * **Docker Compose** pour la conteneurisation des services.
  * **GitHub Actions** pour l'intégration et le déploiement continus (CI/CD).
  * **Proxmox** comme plateforme d'hébergement des conteneurs.
  * **Let's Encrypt** pour la génération et le renouvellement des certificats SSL.

Cette architecture permet de déployer de nouvelles versions de l'application de manière automatique et sécurisée, réduisant les risques d'erreur humaine et assurant une disponibilité maximale du service.

-----

# Modèle de Données

Le modèle de données de QuiZine est au cœur du système, conçu pour supporter toutes les fonctionnalités tout en maintenant l'intégrité et les performances.

## Structure Générale

Le modèle s'articule autour de plusieurs entités principales interconnectées.

## Entités Principales

### Utilisateurs et Relations Sociales

L'entité `user` est centrale et contient les informations essentielles :

  * Informations d'identification (nom d'utilisateur, mot de passe).
  * Image de profil.
  * Statut administratif.

Les relations sociales sont gérées via :

  * `amis` : Relations d'amitié établies.
  * `friend_request` : Demandes d'amitié en attente.
  * `game_request` : Invitations à participer à des sessions de quiz.

### Contenu et Quiz

Les quiz et questions sont les éléments de contenu principaux :

  * `quiz` : Collection de questions avec métadonnées.
  * `question` : Questions individuelles avec leurs caractéristiques.
  * `choice` : Options de réponse pour les questions.
  * `nn_quiz_question` : Table de liaison entre quiz et questions.

### Système de Labels et Évaluations

Un système flexible de catégorisation et d'évaluation a été implémenté :

  * `labelisable` : Entité abstraite permettant d'attribuer des labels à différents objets.
  * `label` : Catégories ou tags associés aux contenus.
  * `nn_label_labelisable` : Association entre labels et objets labelisables.
  * `grade` : Évaluations numériques des contenus par les utilisateurs.

### Sessions et Participations

Le système de jeu est géré via :

  * `session` : Instance d'un quiz en cours.
  * `participation` : Enregistrement de la participation d'un utilisateur à une session.
  * `answers` : Réponses données par un utilisateur à des questions spécifiques.

## Particularités du Modèle

Le modèle présente plusieurs caractéristiques notables :

  * **Polymorphisme via `labelisable`** : L'entité `labelisable` permet d'attribuer des labels et des notes à différents types d'objets de manière uniforme.
  * **Normalisation poussée** : Le modèle évite la duplication de données et maintient l'intégrité référentielle.
  * **Contraintes d'intégrité** : Utilisation extensive de clés étrangères pour garantir la cohérence des données.
  * **Tables de jonction** : Gestion efficace des relations *many-to-many* via des tables intermédiaires.

-----

# Chronologie du Projet

Le développement de QuiZine s'est déroulé sur une période très courte, nécessitant une organisation rigoureuse. Voici les étapes clés :

## Phase de Conception (19 Mai)

La première journée a été dédiée à la définition du projet et à sa conception générale :

  * Brainstorming sur les fonctionnalités et le périmètre.
  * Conception préliminaire du modèle de données.
  * Élaboration des maquettes d'interface utilisateur sur Figma.
  * Choix des technologies et de l'architecture.

Cette phase a établi des bases solides, une vision commune et des objectifs clairs.

## Phase de Développement Initial (20 Mai)

La deuxième journée a marqué le début du développement concret :

### Matinée

  * Configuration des environnements de développement.
  * Mise en place de Supabase comme backend as a service.
  * Initialisation du projet Angular pour le frontend.
  * Création du projet ExpressJS pour l'API backend.
  * Définition des interfaces TypeScript partagées.

### Après-midi

  * Développement des premiers composants Angular.
  * Implémentation de l'authentification avec JWT.
  * Création des migrations initiales de la base de données.
  * Configuration du pipeline CI/CD sur GitHub Actions.

## Phase de Développement Principal (21 Mai)

La troisième journée a vu un avancement significatif du développement :

  * Implémentation complète des routes API avec documentation Swagger.
  * Développement des composants Angular pour les fonctionnalités principales.
  * Finalisation du modèle de données avec toutes les relations.
  * Configuration du déploiement automatisé vers l'infrastructure Proxmox.
  * Mise en place des tests unitaires et d'intégration.

## Phase de Finalisation (22-23 Mai)

Les derniers jours ont été consacrés à la finalisation du projet :

  * Correction des bugs et optimisation des performances.
  * Rédaction de la documentation technique.
  * Préparation de la présentation pour la soutenance.
  * Déploiement de la version finale sur l'infrastructure de production.

-----

# Bilan et Retours d'Expérience

## Points Forts du Projet

Le projet QuiZine a été un succès, avec plusieurs aspects remarquables :

  * **Méthodologie de travail efficace** : L'approche Agile adaptée a permis une progression régulière malgré les contraintes de temps.
  * **Architecture technique solide** : Le choix des technologies et la conception modulaire ont facilité le développement collaboratif.
  * **Déploiement automatisé** : La pipeline CI/CD a assuré un déploiement fiable et rapide.
  * **Modèle de données flexible** : La conception de la base de données a permis d'implémenter toutes les fonctionnalités.

## Difficultés Rencontrées

Plusieurs défis ont été relevés pendant le développement :

  * **Contraintes de temps** : Le calendrier serré a parfois entraîné des compromis.
  * **Complexité du modèle de données** : L'organisation des relations entre entités a nécessité plusieurs itérations.
  * **Intégration de technologies diverses** : La combinaison de multiples *frameworks* et outils a parfois posé des difficultés.
  * **Manque de tests complets** : Les contraintes temporelles ont limité la couverture de tests.

## Retours d'Expérience Individuels

### Côté Frontend (Mariem, Ola, Mathieu)

  * **Mariem** : A trouvé l'apprentissage de nouvelles technologies enrichissant, appréciant la méthodologie de travail structurée. Elle a noté une amélioration notable de ses compétences techniques malgré le temps restreint.
  * **Ola** : A activement contribué au développement frontend et aux tests, s'adaptant aux contraintes du projet et acquérant de nouvelles compétences.
  * **Mathieu** : S'est bien adapté aux contraintes et technologies, acquérant de nouvelles compétences en développement web et contribuant significativement au frontend.

### Côté Backend (Antonin, Raphaël, Emma)

  * **Antonin** : A trouvé difficile de respecter les échéances. Il a eu une expérimentation positive avec TypeScript, mais a rencontré des défis dans l'intégration frontend avec différentes représentations de données. Il a également noté que la structure de la base de données était perfectible et l'organisation des fichiers parfois confuse.
  * **Raphaël** : A contribué au développement backend et aux tests, s'adaptant aux contraintes du projet et acquérant de nouvelles compétences.
  * **Emma** : A trouvé l'apprentissage enrichissant malgré un temps de développement court, découvrant de nouvelles technologies. Elle a apprécié le travail d'équipe et la répartition efficace des tâches, constatant qu'une journée et demie investie dans la conception du modèle de données a permis un gain de temps significatif. Elle regrette cependant le manque de tests unitaires et fonctionnels.

### Chef de Projet (Ethan)

  * **Ethan** : A constaté l'importance d'une séparation claire des responsabilités. Il a géré les défis liés au temps restreint et aux exigences élevées, approfondissant ses connaissances en infrastructure et déploiement. Il a trouvé satisfaction dans son rôle de chef de projet, ayant une vue d'ensemble du développement.

## Retour d'Expérience Collectif

L'expérience collective du projet QuiZine a été très formatrice. La collaboration intense sur une courte période a permis de développer des compétences techniques solides, mais aussi des *soft skills* essentiels comme la communication, la gestion du temps et la résolution de problèmes.

Les principaux enseignements collectifs sont :

  * L'importance d'une conception solide en amont du développement.
  * La valeur d'une communication claire et continue.
  * L'efficacité des outils de gestion de projet pour coordonner le travail.
  * Les bénéfices d'une architecture bien pensée pour faciliter le travail collaboratif.

-----

# Perspectives et Améliorations Futures

Bien que QuiZine soit fonctionnel et réponde aux objectifs initiaux, plusieurs améliorations pourraient être envisagées pour une version future :

## Fonctionnalités à Développer

  * Implémentation complète de la gestion des images de profil.
  * Système de notifications pour les interactions sociales.
  * Mode hors-ligne avec synchronisation ultérieure.
  * Système d'analyse statistique avancée des performances.

## Améliorations Techniques

  * Augmentation de la couverture des tests.
  * Optimisation des performances de la base de données.
  * Mise en place d'un système de cache distribué.
  * Support multilingue complet.

## Évolutions Architecturales

  * Migration vers une architecture microservices.
  * Implémentation d'une API GraphQL en complément de l'API REST.
  * Utilisation de WebSockets pour les fonctionnalités en temps réel.
  * Déploiement sur une infrastructure Kubernetes pour une meilleure scalabilité.

-----

# Conclusion

Le projet QuiZine démontre la capacité d'une équipe à concevoir et développer une application web complète dans un délai très contraint. La combinaison d'une méthodologie de travail efficace, d'une architecture technique solide et d'une collaboration constructive a permis de livrer un produit fonctionnel répondant aux objectifs initiaux.

Les choix technologiques (Angular, TypeScript, Express, Supabase) se sont révélés pertinents, offrant un bon équilibre entre productivité de développement et performances. L'approche **DevOps** avec déploiement automatisé a également été un facteur de réussite important.

Malgré les contraintes et les défis, QuiZine représente une base solide qui pourrait être étendue et améliorée. L'expérience acquise lors de ce projet constitue un patrimoine précieux pour l'ensemble de l'équipe, tant sur le plan technique que méthodologique.

-----

# Annexes

## Glossaire

| Terme | Définition |
| ------------------------------------------ | ---------------------------------------------------------------------- |
| Quiz | Ensemble structuré de questions avec réponses à choix multiples |
| Session | Instance active d'un quiz auquel des utilisateurs peuvent participer |
| Labelisable | Entité pouvant recevoir des labels et des évaluations |
| CI/CD | Continuous Integration/Continuous Deployment - Processus d'automatisation du test et du déploiement |
| Supabase | Plateforme Backend-as-a-Service offrant une alternative open-source à Firebase |
| JWT | JSON Web Token - Standard pour la transmission sécurisée d'informations entre parties |

## Références Techniques

  * Documentation Angular: [https://angular.io/docs](https://angular.io/docs)
  * Documentation TypeScript: [https://www.typescriptlang.org/docs/](https://www.typescriptlang.org/docs/)
  * Documentation ExpressJS: [https://expressjs.com/](https://expressjs.com/)
  * Documentation Supabase: [https://supabase.com/docs](https://supabase.com/docs)
  * Documentation TailwindCSS: [https://tailwindcss.com/docs](https://tailwindcss.com/docs)