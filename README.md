# 🧠 Ontologie pour la Santé Mentale

Bienvenue dans ce projet d'ontologie dédié à la santé mentale ! Ce projet a pour but de modéliser des interactions entre patients, symptômes, troubles psychologiques, tests et interventions, en utilisant les technologies sémantiques (RDF, RDFS, OWL, SPARQL et SWRL). 

---

## 📑 Table des Matières

- [Contexte et Objectifs](#contexte-et-objectifs)
- [Domaines et Modélisation](#domaines-et-mod%C3%A9lisation)
  - [Classes et Sous-classes](#classes-et-sous-classes)
  - [Propriétés et Sous-propriétés](#propri%C3%A9t%C3%A9s-et-sous-propri%C3%A9t%C3%A9s)
  - [Tableau récapitulatif](#tableau-r%C3%A9capitulatif)
- [Namespaces Utilisés](#namespaces-utilis%C3%A9s)
- [Exemples de Requêtes SPARQL](#exemples-de-requ%C3%AAtes-sparql)
- [Structure du Dépôt](#structure-du-d%C3%A9p%C3%B4t)
- [Conclusion](#conclusion)

---

## 🎯 Contexte et Objectifs

Ce projet vise à :
- **Modéliser** les données du domaine de la santé mentale.
- **Exploiter** les technologies sémantiques pour enrichir les inférences et faciliter l’interrogation des données.
- **Améliorer** la granularité des diagnostics et recommandations via une représentation hiérarchique des concepts.

---

## 📚 Domaines et Modélisation

### Classes et Sous-classes

- **Patient**
  - **Adulte**
  - **Enfant**
- **TroublePsychologique**
  - **Neurodéveloppemental**
  - **De humeur**
  - **De personnalité**

### Propriétés et Sous-propriétés

- **aSymptome**
  - **Physique** (symptômes corporels, ex. douleur, fatigue)
  - **Psychologique** (symptômes mentaux, ex. anxiété, tristesse)

De plus, nous avons d'autres propriétés interconnectées dans l'ontologie, notamment :
- **diagnostiquéAvec** : lie un patient à un trouble psychologique.
- **prendsTest** : lie un patient à un test.
- **recommandeIntervention** : lie un trouble psychologique à une intervention.

### Tableau récapitulatif

| **Catégorie**             | **Élément Général**         | **Sous-éléments**                                     |
|---------------------------|-----------------------------|-------------------------------------------------------|
| **Classes : Patient**     | Patient                     | - Adulte<br>- Enfant                                  |
| **Classes : Troubles**    | TroublePsychologique        | - Neurodéveloppemental<br>- De humeur<br>- De personnalité |
| **Propriétés : aSymptome** | aSymptome                   | - Physique<br>- Psychologique                         |

---

## 🔖 Namespaces Utilisés

Pour garantir l'interopérabilité et la conformité aux standards, nous utilisons les namespaces suivants :

- **xsd** : `http://www.w3.org/2001/XMLSchema#`
- **dc** : `http://purl.org/dc/elements/1.1/`
- **foaf** : `http://xmlns.com/foaf/0.1/`
- **rdfs** : `http://www.w3.org/2000/01/rdf-schema#`
- **owl** : `http://www.w3.org/2002/07/owl#`
- **skos** : `http://www.w3.org/2004/02/skos/core#`

Ces namespaces vous permettront de définir les types de données, d'ajouter des métadonnées, et de construire une ontologie robuste et interopérable.

---

## 🔍 Exemples de Requêtes SPARQL

### 1. Patients adultes avec symptômes physiques

```sparql
SELECT ?patient WHERE {
  ?patient a :Adulte .
  ?patient :aSymptomePhysique ?symptome .
}
