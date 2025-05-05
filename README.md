# 🧠 Ontologie pour la Psychologie

Ce projet a pour but de modéliser le domaine de la psychologie en intégrant les concepts suivants :  
1. **Patient** 👤  
2. **Symptômes** 🤒  
3. **Troubles Psychologiques** 🧩  
4. **Test** 📝  
5. **Intervention** 💊  

Les relations principales mises en place sont :  
- **aSymptome** (avec sous-propriétés *Physique* 💪 et *Psychologique* 🧠)  
- **diagnostiqueAvec** (exemple : *Alice diagnostiqueAvec Dépression*)  
- **prendsTest** (exemple : *Alice prendsTest BeckDepressionInventory*)  
- **recommandeIntervention** (exemple : *Dépression recommandeIntervention CBT*)

---

## 📑 Table des Matières

- [Contexte et Objectifs](#contexte-et-objectifs)
- [Modélisation du Domaine](#modélisation-du-domaine)
  - [Classes et Sous-classes](#classes-et-sous-classes)
  - [Propriétés et Sous-propriétés](#propriétés-et-sous-propriétés)
  - [Tableau récapitulatif](#tableau-récapitulatif)
- [Namespaces Utilisés](#namespaces-utilisés)
- [Structure du Dépôt](#structure-du-dépôt)
- [Conclusion](#conclusion)

---

## 🎯 Contexte et Objectifs

Ce projet vise à construire une ontologie détaillée pour la psychologie en utilisant des technologies sémantiques (RDF, RDFS, OWL, SPARQL et SWRL). L'objectif est de :

- **Modéliser** les interactions entre patients, symptômes, troubles, tests et interventions.
- **Exploiter** les inférences pour améliorer l'analyse des données cliniques.
- **Faciliter** l'automatisation des recommandations thérapeutiques.

---

## 📚 Modélisation du Domaine

### 👥 Classes et Sous-classes

#### 1. Personnes 👤
- **Personne**
  - **Patient** - Individu recevant des soins psychologiques
  - **Praticien** - Professionnel de santé mentale
    - **Psychologue** - Spécialiste en psychologie 
    - **Psychiatre** - Médecin spécialisé en psychiatrie
#### 2. Symptômes 🤒
- **Symptome**
  - **SymptomePhysique** - Manifestations physiques (insomnie, fatigue, etc.)
  - **SymptomeCognitif** - Manifestations cognitives (pensées négatives, difficultés de concentration)
  - **SymptomeEmotionnel** - Manifestations émotionnelles (tristesse, anxiété)
#### 3. Troubles Psychologiques 🧩
- **TroublePsychologique**
  - **TroubleAnxieux** - Anxiété généralisée, phobies, etc.
  - **TroubleHumeur** - Dépression, trouble bipolaire, etc.
  - **TroublePsychotique** - Schizophrénie, troubles délirants, etc.
- **Classes composées**:
  - **TroubleAffectif** = TroubleAnxieux ∪ TroubleHumeur
  - **TroubleNonPsychotique** = ¬TroublePsychotique
  - **PatientDepressif** = Patient ∩ ∃aDiagnostic.Depression
#### 4. Tests 📝
- **Test**
  - **TestPersonnalite** - MMPI, Beck Depression Inventory, etc.
  - **TestCognitif** - Tests d'intelligence, d'attention, etc.
  - **TestProjectif** - Rorschach, TAT, etc.
#### 5. Interventions 💊
- **Intervention**
  - **TherapieCognitivoComportementale** (TCC)
  - **TherapiePsychodynamique** (psychanalyse, etc.)
  - **TraitementMedicamenteux** - Utilise des médicaments pour traiter les troubles
#### 6. Médicaments 💊
- **Medicament**
  - **Antidepresseur** - Pour traiter la dépression
  - **Anxiolytique** - Pour réduire l'anxiété
  - **Antipsychotique** - Pour traiter les troubles psychotiques

### 🔗 Propriétés et Sous-propriétés

### Propriétés d'objets
#### Relations Patient-Symptôme-Trouble
- **aSymptome** - Relie un patient à ses symptômes
- **aDiagnostic** - Relie un patient à son diagnostic
- **estAssocieA** - Relie un symptôme à un trouble psychologique

#### Relations Patient-Praticien
- **estMedecinTraitant** - Relie un praticien à son patient (propriété fonctionnelle)
- **aMedecinTraitant** - Relie un patient à son praticien (inverse de estMedecinTraitant)

#### Relations entre Praticiens
- **collaboreAvec** - Relie deux praticiens qui collaborent (propriété symétrique)
- **supervise** - Relie un superviseur à un supervisé (propriété transitive)
- **estSupervisePar** - Inverse de supervise

#### Relations Tests et Interventions
- **administreTest** - Relie un praticien au test qu'il administre
- **aPasseTest** - Relie un patient au test qu'il a passé
- **prescritIntervention** - Relie un praticien à l'intervention qu'il prescrit
- - **prescritMedicament** - limitée aux psychiatres
- **recevoitIntervention** - Relie un patient à l'intervention qu'il reçoit
- **utilise** - Relie un traitement médicamenteux à un médicament
- **cibleTrouble** - Relie une intervention au trouble qu'elle cible

### Propriétés de données

- **nom** - Nom de famille d'une personne
- **prenom** - Prénom d'une personne
- **dateNaissance** - Date de naissance (format dateTime)
- **niveau** - Intensité d'un symptôme (échelle de 1 à 10)
- **dateDebut** - Date d'apparition d'un symptôme
- **score** - Résultat numérique d'un test
- **anneeExperience** - Années d'expérience d'un praticien (0-70)
- **dosage** - Dosage d'un médicament (en mg)

### 📊 Tableau récapitulatif

| **Catégorie**             | **Élément Général**         | **Sous-éléments / Relations**                                                                                                                               |
|---------------------------|-----------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Classes : Patient**     | Patient 👤                  | - Adulte<br>- Enfant                                                                                                                                        |
| **Classes : Symptômes**   | Symptômes 🤒                | (Regroupe l'ensemble des symptômes)                                                                                                                         |
| **Classes : Troubles**    | Trouble Psychologique 🧩     | - Neurodéveloppemental<br>- De humeur<br>- De personnalité                                                                                                  |
| **Classes : Test**        | Test 📝                     | (Différents tests de diagnostic)                                                                                                                            |
| **Classes : Intervention**| Intervention 💊             | (Interventions thérapeutiques)                                                                                                                              |
| **Propriétés : aSymptome**| aSymptome                  | - Physique 💪<br>- Psychologique 🧠                                                                                                                           |
| **Autres Propriétés**     | diagnostiqueAvec            | Lie un Patient à un Trouble Psychologique                                                                                                                   |
|                           | prendsTest                  | Lie un Patient à un Test                                                                                                                                        |
|                           | recommandeIntervention      | Lie un Trouble Psychologique à une Intervention                                                                                                             |
## 📊 Tableau récapitulatif des classes et propriétés

| **Classe**                | **Sous-classes**                                                                 | **Propriétés d'objets**                                                              | **Propriétés de données**                                      |
|---------------------------|-----------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|---------------------------------------------------------------|
| **Personnes 👤**           | **Patient**, **Praticien** (Psychologue, Psychiatre)                               | **estMedecinTraitant** (relie un praticien à un patient)                             | **nom**, **prenom**, **dateNaissance**                         |
| **Symptômes 🤒**           | **SymptomePhysique**, **SymptomeCognitif**, **SymptomeEmotionnel**                 | **aSymptome** (relie un patient à un symptôme)                                       | **niveau** (intensité), **dateDebut**                          |
| **Troubles Psychologiques 🧩** | **TroubleAnxieux**, **TroubleHumeur**, **TroublePsychotique**                      | **estAssocieA** (relie un symptôme à un trouble)                                     | **score** (résultat de test), **dateDebut**                    |
| **Tests 📝**               | **TestPersonnalite**, **TestCognitif**, **TestProjectif**                         | **administreTest** (relie un praticien à un test)                                   | **score** (résultat du test), **anneeExperience** (praticien)  |
| **Interventions 💊**       | **TherapieCognitivoComportementale**, **TherapiePsychodynamique**, **TraitementMedicamenteux** | **prescritIntervention** (relie un praticien à une intervention)                    | **dosage** (en mg)                                             |
| **Médicaments 💊**         | **Antidepresseur**, **Anxiolytique**, **Antipsychotique**                         | **utilise** (relie un traitement médicamenteux à un médicament)                      | **dosage** (en mg)                                             |



---

![santementale](https://github.com/user-attachments/assets/af1855ac-4b36-49db-8f18-c680c970bd45)


## 🌐 Namespaces Utilisés

| Préfixe | URI                                         |
|---------|---------------------------------------------|
| `xsd`   | http://www.w3.org/2001/XMLSchema#            |
| `dc`    | http://purl.org/dc/elements/1.1/             |
| `foaf`  | http://xmlns.com/foaf/0.1/                   |
| `rdfs`  | http://www.w3.org/2000/01/rdf-schema#         |
| `owl`   | http://www.w3.org/2002/07/owl#               |
| `skos`  | http://www.w3.org/2004/02/skos/core#          |

Ces vocabulaires standard assurent l'interopérabilité de l'ontologie avec d'autres systèmes sémantiques.

---

## 🗂 Structure du Dépôt

```plaintext
psychologie-ontology/
├── psych.owl            # Fichier OWL complet de l'ontologie
├── psychologie.rdf      # Export RDF/XML de la modélisation en RDF et RDFS
├── SPARQL.txt           # Fichier contenant les requêtes SPARQL
├── regles_swrl.swrl     # Fichier contenant les règles SWRL
└── README.md            # Documentation et présentation du projet

---
## Conclusion

Cette ontologie pour la psychologie clinique offre un modèle riche et formel pour représenter les connaissances du domaine. Elle permet non seulement d'organiser les informations sur les patients, leurs symptômes et leurs traitements, mais aussi de déduire de nouvelles connaissances à l'aide des capacités d'inférence d'OWL et des règles SWRL.

En exploitant les technologies sémantiques (RDF, RDFS, OWL, SPARQL et SWRL), ce modèle ontologique facilite l'interopérabilité des données cliniques et peut contribuer significativement à l'amélioration des pratiques de santé mentale basées sur les données.
