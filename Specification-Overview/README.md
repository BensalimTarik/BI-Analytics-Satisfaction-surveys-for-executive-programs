
# Projet BI – Enquêtes de satisfaction générale « Cursus Exécutif »

## 1. Présentation du projet

Dans le cadre du suivi de la qualité et de la performance des enseignements et des formations au sein du Groupe C&D, ce projet vise à mettre en place un dispositif structuré d’enquête de satisfaction auprès des étudiants inscrits dans les cursus exécutifs.

Ce dispositif permet de mesurer et de suivre le niveau de satisfaction des étudiants selon plusieurs axes d’analyse, notamment la qualité pédagogique, l’accompagnement, l’information et l’orientation, la logistique ainsi que la valeur perçue de la formation.

L’objectif est de disposer d’une vision consolidée et exploitable de l’expérience étudiante afin d’identifier les principaux points forts, les axes d’amélioration et les leviers d’action.

## 2. Objectifs métier

Le projet répond à six objectifs principaux :

| N° | Objectif spécifique | Indicateur de succès | Cible |
|---|---|---|---|
| O1 | Concevoir et mettre à disposition les formulaires d’enquête de satisfaction selon les différents axes d’analyse définis. | Formulaires validés et disponibles | 100 % des formulaires nécessaires |
| O2 | Automatiser l’envoi des formulaires aux étudiants concernés selon les règles et échéances définies. | Taux d’envoi automatisé des questionnaires | 100 % des étudiants éligibles |
| O3 | Automatiser la collecte et la centralisation des réponses aux enquêtes. | Taux de réponses correctement réceptionnées et enregistrées | ≥ 95 % des réponses soumises |
| O4 | Assurer la transformation, le nettoyage et la préparation des données issues des différentes sources pour leur exploitation analytique. | Taux de données conformes et exploitables | ≥ 95 % de données exploitables |
| O5 | Mettre en place des tableaux de bord interactifs permettant de suivre la satisfaction des étudiants selon les principaux axes d’analyse. | Tableau de bord opérationnel et indicateurs disponibles | 100 % des indicateurs prioritaires |
| O6 | Permettre aux responsables métiers et pédagogiques d’identifier les tendances, points forts et axes d’amélioration à partir des résultats des enquêtes. | Disponibilité des indicateurs et analyses nécessaires à la prise de décision | 100 % des besoins analytiques prioritaires couverts |

## 3. Périmètre fonctionnel et processus métier

| Étape du processus | Fonctionnement cible | Amélioration attendue |
|---|---|---|
| **Collecte et préparation des données** | Mettre en place des traitements automatisés pour extraire les données nécessaires depuis IGOR et les transférer vers une base SQL Server dédiée au projet. Prévoir des contrôles qualité et des règles de transformation afin de garantir la cohérence des données avant leur exploitation. | - Réduire les manipulations manuelles sous Excel.<br>- Fiabiliser et standardiser les données utilisées pour les enquêtes.<br>- Faciliter l’actualisation périodique des données et assurer la traçabilité des traitements. |
| **Gestion et envoi des enquêtes** | Mettre en place des formulaires HTML adaptés aux besoins de chaque marque d’école, avec un identifiant unique permettant d’associer chaque réponse à l’enquête et à la période de formation concernées. Automatiser la préparation des destinataires et l’envoi des questionnaires selon les règles définies. | - Réduire le temps de préparation et d’envoi des enquêtes.<br>- Limiter les erreurs de saisie et les associations incorrectes entre formulaires et périodes de formation.<br>- Améliorer la traçabilité des enquêtes et de leurs destinataires. |
| **Collecte et centralisation des réponses** | Utiliser Azure Logic Apps pour automatiser le traitement des réponses et leur enregistrement dans une base de données dédiée. Mettre en place des contrôles pour vérifier la validité des réponses, limiter les doublons et suivre les erreurs de traitement. | - Supprimer les opérations manuelles de copier-coller dans Excel.<br>- Réduire les erreurs de manipulation.<br>- Centraliser les réponses dans une structure exploitable pour l’analyse et assurer le suivi des traitements. |
| **Analyse et restitution** | Concevoir des rapports Power BI détaillés, organisés en plusieurs pages selon les besoins métier. Structurer le modèle de données selon une architecture en étoile, avec des tables de faits et des dimensions adaptées aux axes d’analyse. | - Améliorer la fiabilité et la cohérence des KPI.<br>- Couvrir les besoins d’analyse prioritaires des parties prenantes.<br>- Faciliter l’analyse de la satisfaction par marque d’école, formation, promotion et axe d’évaluation.<br>- Optimiser les performances d’actualisation et faciliter la maintenance des rapports. |

## 4. Indicateurs clés de performance (KPI)

Les tableaux de bord permettent notamment de suivre les indicateurs suivants :

| KPI | Définition | Formule / règle | Source | Fréquence | Cible | Exigence |
|---|---|---|---|---|---|---|
| **KPI 01 – Nombre de réponses reçues** | Nombre de réponses enregistrées pour une campagne d’enquête. | Comptage des réponses valides reçues, selon les règles de déduplication définies. | Base des réponses | À chaque actualisation BI | Suivi évolutif | BR-05 |
| **KPI 02 – Taux de réponse** | Part des étudiants invités ayant répondu à l’enquête. | (Nombre d’étudiants ayant répondu ÷ Nombre d’étudiants invités) × 100 | Base des réponses et base des invitations | À chaque actualisation BI | ≥ 70 % à titre indicatif | BR-05 |
| **KPI 03 – Nombre de notifications envoyées** | Volume total des invitations et relances transmises aux étudiants. | Comptage des notifications envoyées, par type et par campagne. | Historique des notifications | À chaque actualisation BI | 100 % des notifications planifiées traitées | BR-05 |

## 5. Architecture des données et sources

### 5.1. Sources de données

**Source 1 – IGOR / SQL Server**

Données relatives notamment :
- Aux inscriptions et aux étudiants.
- Aux formations.
- Aux axes d’analyse.
- À l’année scolaire en cours.

L’accès aux données est effectué en lecture seule, selon les autorisations accordées.

**Source 2 – Base SQL Server dédiée Data Analytics**

Cette base contient les données structurées et préparées pour les traitements et les analyses.

Les opérations de lecture et d’écriture sont contrôlées selon les besoins du processus.

### 5.2. Technologies utilisées

- **IGOR :** système source des données.
- **SQL Server :** stockage et centralisation des données.
- **Azure Logic Apps :** automatisation des traitements et de la collecte des réponses.
- **HTML :** conception des questionnaires.
- **Power BI :** modélisation, analyse et visualisation des données.

## 6. Règles de gestion et qualité des données

| ID | Règle | Détail / exemple | Validée par |
|---|---|---|---|
| **RG-01** | Définition et calcul des KPI | Chaque KPI doit disposer d’une définition métier, d’une formule de calcul, d’un périmètre et de règles de filtrage documentés. Les formules doivent être cohérentes avec la section « Indicateurs et KPI » et validées avant leur intégration dans Power BI. | Directeurs des marques d’école, responsables pédagogiques |
| **RG-02** | Automatisation du processus des enquêtes | Le processus est organisé en trois workflows distincts sous Azure Logic Apps : 1. Envoi des questionnaires aux destinataires concernés ; 2. Notification et relance des étudiants n’ayant pas répondu, selon les règles définies ; 3. Réception et centralisation des réponses dans la base de données dédiée. Chaque workflow doit assurer la traçabilité des traitements et la gestion des erreurs. | Directeurs des marques d’école, responsables pédagogiques |
| **RG-03** | Rapprochement des enquêtes et des destinataires | Chaque enquête doit être associée à la période de formation (PF), à la formation, à la marque d’école et au groupe d’apprenants concernés. Le rapprochement doit s’appuyer sur des identifiants fiables issus des données de référence. Toute association manquante ou ambiguë doit être signalée avant l’envoi. | Directeurs des marques d’école, responsables pédagogiques |
| **RG-04** | Gestion des réponses et des doublons | Chaque réponse doit être associée à une enquête identifiable. Les règles concernant les réponses multiples, les soumissions répétées et la prise en compte de la dernière réponse doivent être définies avant le calcul des KPI. | Directeurs des marques d’école, responsables pédagogiques |
| **RG-05** | Gestion des relances | Une relance est déclenchée uniquement pour les destinataires éligibles n’ayant pas répondu à l’enquête concernée, dans la limite du nombre de relances défini. Le statut d’envoi et de réponse doit être enregistré. | Directeurs des marques d’école, responsables pédagogiques |
| **RG-06** | Accès aux résultats | Les utilisateurs consultent les résultats correspondant à leur périmètre de responsabilité, selon les habilitations accordées. Les réponses individuelles et les commentaires sont accessibles uniquement aux personnes autorisées. | Directeurs des marques d’école, responsables pédagogiques |

---

*Projet réalisé dans le cadre de l’analyse de la satisfaction des étudiants du groupe Compétences & Développement.*
