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

- **Patient** 👤  
  - **Adulte**  
  - **Enfant**
- **Symptômes** 🤒  
  *Représente l'ensemble des symptômes observés chez un patient.*
- **Troubles Psychologiques** 🧩  
  - **Neurodéveloppemental**  
  - **De humeur**  
  - **De personnalité**
- **Test** 📝  
  *Regroupe les différents tests de diagnostic utilisés.*
- **Intervention** 💊  
  *Regroupe les interventions thérapeutiques.*

### 🔗 Propriétés et Sous-propriétés

- **aSymptome**  
  - **Physique** 💪  
  - **Psychologique** 🧠
- **diagnostiqueAvec**  
  *Lie un Patient à un Trouble Psychologique (ex : Alice diagnostiqueAvec Dépression).*
- **prendsTest**  
  *Lie un Patient à un Test (ex : Alice prendsTest BeckDepressionInventory).*
- **recommandeIntervention**  
  *Lie un Trouble Psychologique à une Intervention (ex : Dépression recommandeIntervention CBT).*

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

---

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
├── ontology.owl         # Fichier OWL complet de l'ontologie
├── rdf_model.rdf        # Export RDF/XML de la modélisation en RDF et RDFS
├── requetes_sparql.txt  # Fichier contenant les requêtes SPARQL
├── regles_swrl.swrl     # Fichier contenant les règles SWRL
└── README.md            # Documentation et présentation du projet
