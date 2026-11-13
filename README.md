# <img src="assets/logo.png" alt="class logo" class="logo" width="120"/> R5.Real.10 - Nouveaux paradigmes de base de données

## BUT Informatique - 3ème année - Parcours A « Réalisation d'applications : conception, développement, validation » - IUT Aix-Marseille (département Informatique)

---

> [!IMPORTANT]
> **À faire avant la première séance (semaine du 23 novembre 2026)**
> 1. Avoir un **compte GitHub** et savoir s'y connecter (mot de passe et double authentification).
> 2. Faire reconnaître son **statut étudiant** sur [GitHub Education](https://education.github.com/discount_requests/application), avec ce même compte.
> 3. Vers le **18 novembre**, accepter l'invitation à rejoindre l'organisation **`IUTInfoAix-R510-2026`**, reçue sur votre **adresse universitaire** (valable 7 jours), avec ce même compte. Puis ouvrir le [lien d'accueil Classroom 50](https://classroom50.org/IUTInfoAix-R510-2026/r510/onboard) et s'y connecter avec ce même compte.
> 4. Régler sur <https://github.com/settings/codespaces> une mise en veille de 30 minutes au plus et une durée de conservation de 7 jours.
>
> Chaque étape est détaillée dans la section [Environnement technique](#environnement-technique).

---

## 📋 Informations générales

- **Intitulé** : R5.Real.10 - Nouveaux paradigmes de base de données
- **Semestre** : S5 (année BUT3), parcours A
- **Volume horaire PN** : 25 h (dont 8 h de TP)
- **Emploi du temps 2026-2027** : 32 h, soit **8 séances de 4 h** en salle machine (5 séances de TP et 3 séances de projet), du 23 novembre au 17 décembre 2026
- **Responsable** : [Sébastien NEDJAR](mailto:sebastien.nedjar@univ-amu.fr)
- **Équipe pédagogique** :
  - [Sébastien NEDJAR](mailto:sebastien.nedjar@univ-amu.fr) - groupe **GA1** (A1-1, A1-2)
  - [Leïla SAKLI MILED](mailto:leila.SAKLI@univ-amu.fr) - groupe **GA2** (A2-1, A2-2)
- **Format des séances** : blocs de 4 h en salle machine, par groupe. Les deux groupes suivent **exactement les mêmes TP et le même projet**.
- **Ressource officielle** : [Annexe 15 du PN BUT Informatique 2022, mis à jour en 2023 - fiche R5.Real.10 p. 160](https://www.enseignementsup-recherche.gouv.fr/sites/default/files/2023-12/informatique-30855.pdf#page=160)
- **Mots-clés officiels** : Paradigme non relationnel - NoSQL

---

## 🎯 Objectifs pédagogiques

### Objectif général (extrait du PN)

> *L'objectif de cette ressource est d'appréhender les paradigmes non relationnels de base de données intégrés pour le développement d'applications sur des supports spécifiques. Cette ressource développe les différentes implémentations des données dans l'entreprise qui pourront être utilisée dans des développements d'applications spécifiques.*

En pratique, le module étudie **deux paradigmes non relationnels** :

- le modèle **document**, avec **MongoDB** (requêtes, agrégation, modélisation, index) ;
- le modèle **graphe**, avec **Neo4j** et le langage **Cypher** (motifs, chemins, recommandation).

Les autres familles (clé-valeur, colonnes, vectoriel, multi-modèle) sont situées en cours. L'objectif est de savoir **choisir le modèle adapté aux requêtes** et de l'intégrer dans une application.

### Compétences BUT ciblées

| Compétence | Intitulé |
|---|---|
| **Compétence 1 - Réaliser** | Développer - c'est-à-dire concevoir, coder, tester et intégrer - une solution informatique pour un client |
| **Compétence 2 - Optimiser** | Proposer des applications informatiques optimisées en fonction de critères spécifiques : temps d'exécution, précision, consommation de ressources |

### Apprentissages critiques (AC)

> [!NOTE]
> **Lecture des codes d'apprentissages critiques** : dans le PN BUT Informatique, le code `ACLC.NN` se décompose ainsi :
> - `L` = niveau (1 = BUT1, 2 = BUT2, 3 = BUT3)
> - `C` = numéro de la compétence
> - `NN` = numéro de l'AC dans cette compétence à ce niveau

Les apprentissages critiques officiellement rattachés à R5.Real.10 :

- **AC31.02** - Faire évoluer une application existante *(projet : faire évoluer le squelette fourni)*
- **AC31.03** - Intégrer des solutions dans un environnement de production *(environnement Codespaces reproductible, conteneurs MongoDB et Neo4j, index et analyse des plans d'exécution)*
- **AC32.03** - Choisir et utiliser des bibliothèques et méthodes dédiées au domaine d'application (imagerie, immersion, intelligence artificielle, jeux vidéos, parallélisme, calcul formel...) *(choisir le paradigme selon les requêtes, pilote Java MongoDB)*

### Savoirs de référence (descriptif PN)

- Concepts, structures de données et langages d'interrogation (par ex. : base de données mobiles, embarquées, objets, NoSQL - déductives, clés-valeurs, **documents**, colonnes, **graphe**...)

### SAÉ concernée par cette ressource

- **SAÉ 5.Real.01** - Développement avancé : développer en équipe une application qui doit « utiliser des API complexes (framework, ...), interroger une base de données et s'appuyer sur un serveur ».

### Acquis d'apprentissage détaillés (implémentation 2026-2027)

À l'issue de cette ressource, vous serez capable de :

1. **Justifier** le choix d'un paradigme (relationnel, document, graphe) à partir des requêtes attendues *(AC32.03)*
2. **Manipuler** des documents MongoDB : CRUD, documents imbriqués et tableaux, opérateurs de requête *(AC31.03)*
3. **Analyser** des données avec le pipeline d'agrégation : `$match`, `$group`, `$unwind`, `$lookup`, `$bucket`, `$facet`, fenêtres (`$setWindowFields`), dates (`$dateTrunc`), requêtes géospatiales *(AC32.03)*
4. **Concevoir** un modèle document : embarquer ou référencer, patterns de conception (Subset, Computed, Bucket...), résultats enregistrés par `$merge`, collections time series et rétention (TTL), validation de schéma (`$jsonSchema`) *(AC31.02, AC32.03)*
5. **Optimiser** les requêtes : index simples et composés, `explain()`, contraintes et `PROFILE` côté graphe *(AC31.03)*
6. **Modéliser** un graphe de propriétés à partir d'un schéma relationnel et l'interroger en **Cypher** : motifs, agrégation, chemins de longueur variable, recommandation *(AC32.03)*
7. **Intégrer** MongoDB dans une application **Java** (API REST **Javalin**, pilote MongoDB) et, en bonus, modéliser une partie de ses données dans Neo4j *(AC31.02, AC31.03)*

---

## 📚 Prérequis

### Ressources BUT mobilisées

- **R1.05** (Introduction aux bases de données et SQL), **R2.06** (Exploitation d'une base de données), **R3.07** (SQL dans un langage de programmation), **R4.03** (Qualité et au-delà du relationnel) : modèle relationnel, SQL, accès aux données depuis un programme
- **R2.01** (Développement orienté objets) et la suite du parcours : programmation **Java**
- **R2.03** (Qualité de développement) : Git, tests unitaires

### Compétences techniques

- Écrire des requêtes SQL avec jointures et agrégations
- Programmer en Java (classes, collections, exceptions) et lire une trace d'exécution
- Utiliser Git et GitHub (clone, commit, push, branches, pull requests)
- Lire et écrire du JSON

### Environnement technique

> [!IMPORTANT]
> **Tout le travail se fait dans GitHub Codespaces**, dans le navigateur. Vous n'avez rien à installer, ni sur les postes de l'IUT ni sur votre machine : chaque TP fournit un environnement préconfiguré, bases de données comprises.

- **GitHub Codespaces** : environnement de développement en ligne, sur la machine **2 cœurs** prévue pour le module
- **MongoDB 9.0** (TP1 à TP3, projet) et **Neo4j Community 2026** (TP4, bonus du projet) : lancés dans le codespace du TP concerné
- **VS Code** + extensions **MongoDB for VS Code** (playgrounds) et **Neo4j**
- **Java 25**, **Maven** (via le wrapper `./mvnw` fourni), **Javalin** et le pilote Java MongoDB pour le projet (pilote Neo4j facultatif, pour le bonus)
- **Classroom 50** ([classroom50.org](https://classroom50.org/)), qui remplace GitHub Classroom : vous vous y connectez avec votre compte GitHub pour accepter les TP et suivre vos rendus

#### Votre compte GitHub et votre quota Codespaces

Les codespaces sont décomptés de **votre quota personnel GitHub**, celui du compte qui crée le codespace. Le quota se compte en **heures-cœur** : une heure sur une machine 2 cœurs consomme 2 heures-cœur.

| Compte | Quota mensuel | Soit, en 2 cœurs |
|---|---|---|
| Compte gratuit | 120 heures-cœur et 15 Go de stockage | environ 60 h |
| Statut étudiant reconnu (GitHub Education) | 180 heures-cœur et 20 Go de stockage | environ 90 h |

Pour que ce quota ait les meilleures chances de suffire jusqu'à la fin du module :

1. **Faites reconnaître votre statut étudiant** sur [GitHub Education](https://education.github.com/discount_requests/application). La validation peut prendre quelques jours : si elle n'est pas arrivée le 23/11, commencez quand même, le quota gratuit suffit pour novembre.
2. **Gardez la machine 2 cœurs** : une machine 4 cœurs consomme le quota deux fois plus vite.
3. **Supprimez le codespace d'un TP une fois sa date limite passée**, après avoir vérifié sur github.com que vos derniers commits y sont. La suppression efface les modifications non poussées et le contenu des bases, mais pas les fichiers poussés. Un codespace arrêté continue d'occuper de l'espace de stockage.
4. Sur <https://github.com/settings/codespaces>, réglez une **mise en veille** de 30 minutes au plus et une **durée de conservation** de 7 jours.

Le quota se renouvelle chaque mois et il est **commun à tous vos usages de Codespaces**, y compris dans d'autres modules. S'il est épuisé, GitHub bloque vos codespaces jusqu'au mois suivant : **prévenez immédiatement votre enseignant**.

#### Rejoindre l'organisation du module

Vers le **18 novembre 2026**, vous recevrez sur votre **adresse universitaire** une invitation GitHub à rejoindre l'organisation **`IUTInfoAix-R510-2026`**. Sans elle, vous ne pourrez pas récupérer les TP.

- Votre compte GitHub n'a pas besoin d'utiliser votre adresse universitaire. Mais **acceptez l'invitation avec le compte dont vous avez fait reconnaître le statut étudiant** : c'est son quota qui sera décompté.
- L'invitation est valable **7 jours**. Si elle a expiré ou si vous ne la trouvez pas (pensez aux spams), signalez-le en début de première séance.
- Une fois l'invitation acceptée, ouvrez le **lien d'accueil Classroom 50** : <https://classroom50.org/IUTInfoAix-R510-2026/r510/onboard>. Connectez-vous avec le même compte GitHub : vous arrivez sur la page de la classe, où apparaîtront les TP.

---

## 📖 Programme détaillé

### Calendrier 2026-2027

Le module se déroule sur **4 semaines**, à raison de **2 séances de 4 h par semaine et par groupe**. Les jours et horaires changent d'une semaine à l'autre et d'un groupe à l'autre : **consultez ADE**.

| Semaine | Séance | Contenu |
|---|---|---|
| Sem. du 23/11/2026 | S1 | **TP1** MongoDB - documents et CRUD |
| | S2 | **TP1** MongoDB (suite) - documents imbriqués, tableaux, initiation à l'agrégation |
| Sem. du 30/11/2026 | S3 | **TP2** MongoDB - requêtes avancées, pipeline d'agrégation, index, géospatial |
| | S4 | **TP3** MongoDB - modéliser à partir des requêtes, patterns de conception, séries temporelles, validation |
| Sem. du 7/12/2026 | S5 | **TP4** Neo4j - du relationnel au graphe, Cypher |
| | S6 | **Projet** - lancement, modèle de données, chargement des données |
| Sem. du 14/12/2026 | S7 | **Projet** - agrégations, API REST, index ; module graphe en bonus |
| | S8 | **Projet** - finalisation et **questions individuelles** (dernière séance au plus tard le jeudi 17/12) |

Les **dates limites de rendu** sont indiquées dans l'énoncé de chaque TP.

### Supports de cours

Chaque séance commence par un **point cours** qui présente les notions à connaître avant d'attaquer le TP. Les supports sont en ligne, au fur et à mesure : [page des points cours](https://iutinfoaix-r510.github.io/cours/).

| Séance | Point cours |
|---|---|
| S1 | [La ressource, MongoDB et le CRUD](https://iutinfoaix-r510.github.io/cours/s1-ressource-et-mongodb.html) ([PDF](https://iutinfoaix-r510.github.io/cours/s1-ressource-et-mongodb.pdf)) |
| S2 | [Documents imbriqués, tableaux et premiers pipelines](https://iutinfoaix-r510.github.io/cours/s2-imbrication-tableaux-agregation.html) ([PDF](https://iutinfoaix-r510.github.io/cours/s2-imbrication-tableaux-agregation.pdf)) |
| S3 | [Requêtes avancées, agrégation et index](https://iutinfoaix-r510.github.io/cours/s3-requetes-avancees-agregation-index.html) ([PDF](https://iutinfoaix-r510.github.io/cours/s3-requetes-avancees-agregation-index.pdf)) |
| S4 | [Modéliser à partir des requêtes, patterns de conception](https://iutinfoaix-r510.github.io/cours/s4-modelisation-patterns.html) ([PDF](https://iutinfoaix-r510.github.io/cours/s4-modelisation-patterns.pdf)) |
| S5 | [Du relationnel au graphe : Neo4j et Cypher](https://iutinfoaix-r510.github.io/cours/s5-graphe-neo4j-cypher.html) ([PDF](https://iutinfoaix-r510.github.io/cours/s5-graphe-neo4j-cypher.pdf)) |

### Travaux pratiques

> [!IMPORTANT]
> **Accès aux TP** : chaque séance commence par l'**énoncé en ligne** du TP, lien « Énoncé » du tableau ci-dessous. Il explique comment récupérer votre dépôt et ouvrir votre codespace. Les liens d'acceptation sont dans le même tableau. Chaque TP s'ouvre au début de la semaine où il commence (TP1 : lundi 23 novembre à 8 h) ; avant, la page indique « This assignment is locked ». Accepter un TP crée votre dépôt personnel **privé** dans l'organisation `IUTInfoAix-R510-2026`, que vous ouvrez ensuite dans un codespace.

| TP | Thème | Séances | Accès |
|----|-------|---------|-------|
| **TP1** | MongoDB : documents, CRUD, documents imbriqués, initiation à l'agrégation | S1-S2 (8 h) | [Énoncé](https://iutinfoaix-r510.github.io/tp1/) · Cours [S1](https://iutinfoaix-r510.github.io/cours/s1-ressource-et-mongodb.html), [S2](https://iutinfoaix-r510.github.io/cours/s2-imbrication-tableaux-agregation.html) · [Accepter le TP1](https://classroom50.org/IUTInfoAix-R510-2026/r510/assignments/tp1/accept) |
| **TP2** | MongoDB : requêtes avancées, fenêtres, pipeline d'agrégation, index, géospatial, pilote Java | S3 (4 h) | [Énoncé](https://iutinfoaix-r510.github.io/tp2/) · Cours [S3](https://iutinfoaix-r510.github.io/cours/s3-requetes-avancees-agregation-index.html) · [Accepter le TP2](https://classroom50.org/IUTInfoAix-R510-2026/r510/assignments/tp2/accept) |
| **TP3** | MongoDB : modéliser à partir des requêtes, patterns de conception, `$merge`, séries temporelles et TTL, validation `$jsonSchema`, pilote Java | S4 (4 h) | [Énoncé](https://iutinfoaix-r510.github.io/tp3/) · Cours [S4](https://iutinfoaix-r510.github.io/cours/s4-modelisation-patterns.html) · [Accepter le TP3](https://classroom50.org/IUTInfoAix-R510-2026/r510/assignments/tp3/accept) |
| **TP4** | Neo4j : du relationnel au graphe, Cypher, chemins, recommandation | S5 (4 h) | [Énoncé](https://iutinfoaix-r510.github.io/tp4/) · Cours [S5](https://iutinfoaix-r510.github.io/cours/s5-graphe-neo4j-cypher.html) · [Accepter le TP4](https://classroom50.org/IUTInfoAix-R510-2026/r510/assignments/tp4/accept) |
| **Projet** | Application en équipe : Java, Javalin, MongoDB ; bonus Neo4j | S6-S8 (12 h) | ⏳ À venir |

Les TP 1 à 4 se font dans des **playgrounds** (fichiers `.mongodb.js` pour MongoDB, `.cypher` pour Neo4j) : chaque exercice a son emplacement, vous y écrivez et exécutez vos requêtes directement dans VS Code. Les TP2 et TP3 se terminent par une partie en Java (pilote MongoDB et Javalin), dans un projet Maven fourni.

Un même domaine sert de fil conducteur : la **médiathèque** du TP1 (modèle document) est reprise dans le TP4 (modèle graphe), pour comparer les deux paradigmes sur les mêmes questions.

#### Rendre son travail

- Rendre un TP, c'est **commiter, pousser**, puis lancer la **commande de rendu** indiquée dans la section « Rendre son travail » de chaque énoncé.
- **Ne renommez jamais vos dépôts** de TP ou de projet : Classroom 50 ne les retrouverait plus.
- Après la date limite, un rendu est marqué **en retard** ; les conséquences et la date de clôture sont précisées dans chaque énoncé.

#### Errata

Une fois un TP publié, son énoncé n'est plus modifié dans les dépôts déjà créés. Les corrections éventuelles sont listées ici.

*Aucun erratum pour l'instant.*

### Projet (S6-S8)

**Sujet** : présenté au lancement du projet. Le projet se réalise en **équipe**.

- **Pile technique imposée** : **Java 25** au minimum (la dernière version LTS), Maven par son wrapper (`./mvnw`), **Javalin** (API REST), **MongoDB** (pilote Java), un **serveur MCP** que vous implémentez et qu'un agent IA interroge, front web léger. Un **squelette fonctionnel est fourni** : vous le faites évoluer.
- **Attendus** : une quête principale commune (modèle de données document justifié, pipelines d'agrégation, index, API REST, outils MCP, tableau de bord) et des quêtes secondaires au choix, chacune avec un indice de difficulté ; une documentation d'architecture.
- **Bonus graphe** : un module **Neo4j** facultatif (le « trésor »), relié aux données MongoDB. Il rapporte des points supplémentaires.
- **Rendu** : par tag `submit/…` (commande `r510-rendre`), **cinq rendus au plus** ; le dernier poussé avant la date limite est noté.
- **Questions individuelles et détecteur d'IA** : à la dernière séance, chacun répond à des questions sur le code de son équipe, et un détecteur d'IA est appliqué au code rendu. Les questions individuelles et les contributions pondèrent la note d'équipe pour chaque étudiant ; le détecteur d'IA peut déclencher un entretien (voir [Projet - pondération individuelle](#projet---pondération-individuelle)).
- Les équipes sont constituées **à l'intérieur de chaque groupe**, avant la séance S6 ; les modalités sont données en séance. Le projet se fait dans un **dépôt d'équipe**. L'énoncé détaillé et le barème complet sont publiés au lancement du projet.

---

## 🎓 Philosophie pédagogique

### Un environnement unique et reproductible

Tout le monde travaille dans le même environnement : un codespace préconfiguré par TP, avec les mêmes versions de MongoDB, Neo4j et Java. Fini le « ça marche sur ma machine » : une requête que vous écrivez s'exécutera dans le même environnement chez l'enseignant.

### Construire ses requêtes étape par étape

Chaque exercice se traite **une requête à la fois** : écrire, exécuter, lire le résultat, corriger. Une requête complexe (pipeline d'agrégation, motif Cypher) se construit morceau par morceau : on ajoute une étape, on regarde le résultat intermédiaire, puis on ajoute la suivante.

### Utilisation de l'IA

- ✅ L'IA (Copilot Chat ou autre) est **autorisée comme tuteur** : comprendre un concept, un message d'erreur, un opérateur, comparer deux approches.
- ❌ Lui faire écrire la requête ou le code à votre place vous prive de l'apprentissage visé.
- Dans le projet, **l'usage de l'IA doit être documenté** dans le dépôt de l'équipe.
- **Pourquoi c'est essentiel** : dans le projet, des **questions individuelles** vérifient que chacun a réellement fait son travail, et un **détecteur d'IA** est appliqué au code rendu. Vous devez être capable d'expliquer et de modifier tout ce que vous revendiquez.

### Workflow professionnel (projet)

- Dépôt d'équipe, **branches** thématiques et **pull requests**
- **Revue de code** entre coéquipiers avant de fusionner
- Commits clairs et réguliers : l'historique Git sert à apprécier la contribution de chacun

---

## 📊 Évaluations

| Contrôle | Poids | Modalité | Description |
|----------|-------|----------|-------------|
| **CC - TP** | **40 %** | Autograding | TP1 16 %, TP2 8 %, TP3 8 %, TP4 8 % |
| **Projet** | **60 %** | Dépôt d'équipe + séance S8 | Note d'équipe (bonus graphe compris), pondérée pour chaque étudiant par les questions individuelles et les contributions ; le détecteur d'IA peut déclencher un entretien |

### CC - Travaux pratiques (40 %)

Le poids de chaque TP est proportionnel à son nombre de séances. Chaque TP est évalué par **autograding** :

- à chaque rendu, des **tests automatiques** exécutent vos requêtes sur une base de test (MongoDB ou Neo4j) et vérifient leurs résultats ;
- votre **score s'affiche dans Classroom 50** : vous savez quels exercices sont validés et pouvez corriger avant la date limite ;
- la note retenue est celle de votre **dernier rendu** dans les délais fixés par l'énoncé ;
- l'équipe pédagogique **vérifiera aléatoirement** une partie des rendus (réponses écrites en dur, recopie) et ajustera la note en conséquence.

### Projet - note d'équipe

**Barème** sur 100 :

| Critère | Points |
|---|---|
| Quête principale : les sept missions communes (données, API, outils MCP, vues du tableau de bord), vérifiées par le correcteur automatique et par une courte relecture | 40 |
| Quêtes secondaires : les trois meilleures parmi celles déclarées (6, 9, 12 ou 15 points selon la difficulté), multipliées par un coefficient de cohérence | jusqu'à 25 |
| Note technique et artistique : qualité technique (20) et aboutissement et cohérence du rendu (15), sur des critères observables | 35 |
| **Bonus graphe** (module Neo4j, le « trésor ») | jusqu'à +10, note plafonnée à 100 |

Une équipe qui accumule des quêtes difficiles sans cohérence d'ensemble est moins bien notée qu'une équipe qui livre des quêtes simples dans un rendu cohérent : la cohérence multiplie les points des quêtes secondaires. Le détail (formules, critères, cas des binômes) est publié avec l'énoncé du projet.

### Projet - pondération individuelle

La note d'équipe est pondérée pour chaque étudiant. Rien ne s'ajoute à part : les éléments ci-dessous servent à vérifier la réalité du travail de chacun.

**Note individuelle** = min(100, note d'équipe × coefficient). Le coefficient est compris entre 0,6 et 1,1 : il vaut 0,6 + 0,5 × q, où q, compris entre 0 et 1, est fait pour 70 % des questions individuelles et pour 30 % des contributions.

- **Questions individuelles** pendant la dernière séance (S8), environ 6 minutes par étudiant, sans présentation ni jury : vous expliquez une partie du code de votre équipe dont vous êtes auteur ou relecteur dans l'historique Git, puis vous la modifiez devant l'enseignant (ajouter un filtre, un index...). Ces questions ne donnent pas la note finale, elles entrent dans la pondération.
- **Contributions** : au moins une pull request significative et une revue de la pull request d'un coéquipier. L'historique Git est lu de manière **qualitative** : on ne compte pas les commits.
- **Détecteur d'IA** : un filtre de détection d'IA est appliqué au code rendu. Il ne modifie pas directement la note : un résultat suspect déclenche un **entretien** avec l'enseignant, où vous devez expliquer et modifier le code concerné.
- Le travail livré après S8 et avant la date limite compte pleinement dans la note d'équipe.

> [!NOTE]
> Les deux groupes utilisent les **mêmes grilles** et la **même banque de questions**. Une partie des copies est corrigée par les deux enseignants pour harmoniser les notes.

---

## 📝 Règles

### Absences

- Justificatif sous 48 h
- Au-delà de 20 % d'absence : défaillance
- Les TP se faisant dans Codespaces, une séance manquée se rattrape avant la date limite du TP. Une absence justifiée à la séance S8 donne lieu à des questions individuelles reprogrammées avec l'enseignant de votre groupe.

### Plagiat et intégrité

- Code et requêtes originaux exigés ; les sources utilisées doivent être citées
- Collaboration encouragée, copie sanctionnée
- Modifier le correcteur automatique ou les fichiers `.github/` d'un dépôt, supprimer une Release ou recopier les résultats attendus au lieu de les calculer est considéré comme une **fraude** et pourra donc conduire à une sanction, comme l'exclusion, conformément aux M3C
- Usage de l'IA à documenter dans le projet

### Adaptations pédagogiques

Étudiants en situation de handicap, sportifs de haut niveau : contactez le responsable en début de module.

---

## 🛠️ Ressources techniques

### Dépôts GitHub (organisation [`IUTInfoAix-R510`](https://github.com/IUTInfoAix-R510))

- [`syllabus`](https://github.com/IUTInfoAix-R510/syllabus) - ce document, avec les liens des TP et les errata
- [`cours`](https://github.com/IUTInfoAix-R510/cours) - supports des points cours, [en ligne](https://iutinfoaix-r510.github.io/cours/)
- Vos dépôts de TP et de projet : organisation [`IUTInfoAix-R510-2026`](https://github.com/IUTInfoAix-R510-2026) (privés)

### Documentation officielle

- [MongoDB Manual](https://www.mongodb.com/docs/manual/)
- [MongoDB : pipeline d'agrégation](https://www.mongodb.com/docs/manual/core/aggregation-pipeline/)
- [MongoDB for VS Code](https://www.mongodb.com/docs/mongodb-vscode/)
- [Pilote Java MongoDB](https://www.mongodb.com/docs/drivers/java/sync/current/)
- [MongoDB University](https://learn.mongodb.com/) - cours gratuits
- [Neo4j Cypher Manual](https://neo4j.com/docs/cypher-manual/current/)
- [Neo4j GraphAcademy](https://graphacademy.neo4j.com/) - cours gratuits
- [Javalin](https://javalin.io/documentation)
- [GitHub Codespaces](https://docs.github.com/fr/codespaces)

### Bibliographie

- *MongoDB: The Definitive Guide* (3rd Edition) - Shannon Bradshaw, Eoin Brazil, Kristina Chodorow
- *Graph Databases* (2nd Edition) - Ian Robinson, Jim Webber, Emil Eifrem

---

## 📞 Contact

- **Responsable** : [Sébastien NEDJAR](mailto:sebastien.nedjar@univ-amu.fr)
- **Groupe GA2** : [Leïla SAKLI MILED](mailto:leila.SAKLI@univ-amu.fr)
- **Questions sur le module** : via les [issues GitHub du syllabus](https://github.com/IUTInfoAix-R510/syllabus/issues)
- **Questions d'ordre privé** : e-mail à l'enseignant de votre groupe

---

*Ce syllabus peut évoluer selon la progression des groupes et les contraintes institutionnelles. Les modifications importantes sont signalées dans ce document et annoncées en séance.*
