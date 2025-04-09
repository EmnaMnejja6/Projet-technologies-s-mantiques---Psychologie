# 🧠 Ontologie pour la Psychologie

Ce projet a pour but de modéliser le domaine de la psychologie en intégrant les concepts suivants :
1. **Patient** 👤
2. **Symptômes** 🤒
3. **Troubles Psychologiques** 🧩
4. **Test** 📝
5. **Intervention** 💊

Les relations principales mises en place sont :
- **aSymptome** (avec sous-propriétés *Physique* 💪 et *Psychologique* 🧠)
- **diagnostiquéAvec** (exemple : *Alice diagnostiquéAvec Dépression*)
- **prendsTest** (exemple : *Alice prendsTest BeckDepressionInventory*)
- **recommandeIntervention** (exemple : *Dépression recommandeIntervention CBT*)

---

## 📑 Table des Matières

- [Contexte et Objectifs](#contexte-et-objectifs)
- [Modélisation du Domaine](#mod%C3%A9lisation-du-domaine)
  - [Classes et Sous-classes](#classes-et-sous-classes)
  - [Propriétés et Sous-propriétés](#propri%C3%A9t%C3%A9s-et-sous-propri%C3%A9t%C3%A9s)
  - [Tableau récapitulatif](#tableau-r%C3%A9capitulatif)
- [Namespaces Utilisés](#namespaces-utilis%C3%A9s)
- [Exemples de Requêtes SPARQL](#exemples-de-requ%C3%AAtes-sparql)
- [Structure du Dépôt](#structure-du-d%C3%A9p%C3%B4t)
- [Conclusion](#conclusion)

---

## 🎯 Contexte et Objectifs

Ce projet vise à construire une ontologie détaillée pour la santé mentale en utilisant des technologies sémantiques (RDF, RDFS, OWL, SPARQL, et SWRL). L'objectif est de :

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
  *(Représente l'ensemble des symptômes observés chez un patient.)*
- **Troubles Psychologiques** 🧩  
  - **Neurodéveloppemental**  
  - **De humeur**  
  - **De personnalité**
- **Test** 📝  
  *(Regroupe les différents tests de diagnostic utilisés.)*
- **Intervention** 💊  
  *(Regroupe les interventions thérapeutiques.)*

### 🔗 Propriétés et Sous-propriétés

- **aSymptome**  
  - **Physique** 💪  
  - **Psychologique** 🧠
- **diagnostiquéAvec**  
  *(Lie un Patient à un Trouble Psychologique, ex. : Alice diagnostiquéAvec Dépression)*
- **prendsTest**  
  *(Lie un Patient à un Test, ex. : Alice prendsTest BeckDepressionInventory)*
- **recommandeIntervention**  
  *(Lie un Trouble Psychologique à une Intervention, ex. : Dépression recommandeIntervention CBT)*

### 📊 Tableau récapitulatif

| **Catégorie**             | **Élément Général**         | **Sous-éléments / Relations**                                                                                                                               |
|---------------------------|-----------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Classes : Patient**     | Patient 👤                  | - Adulte<br>- Enfant                                                                                                                                        |
| **Classes : Symptômes**   | Symptômes 🤒                | (Regroupe l'ensemble des symptômes)                                                                                                                         |
| **Classes : Troubles**    | TroublePsychologique 🧩     | - Neurodéveloppemental<br>- De humeur<br>- De personnalité                                                                                                  |
| **Classes : Test**        | Test 📝                     | (Différents tests de diagnostic)                                                                                                                            |
| **Classes : Intervention**| Intervention 💊             | (Interventions thérapeutiques)                                                                                                                              |
| **Propriétés : aSymptome**| aSymptome                  | - Physique 💪<br>- Psychologique 🧠                                                                                                                           |
| **Autres Propriétés**     | diagnostiquéAvec            | Lie un Patient à un Trouble Psychologique                                                                                                                   |
|                           | prendsTest                  | Lie un Patient à un Test                                                                                                                                        |
|                           | recommandeIntervention      | Lie un Trouble Psychologique à une Intervention                                                                                                             |

---
### Visualisation
![psychologie](https://github.com/user-attachments/assets/b4a4c838-cd25-4661-a337-8e9655b1224b)

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

## 🔍 Exemples de Requêtes SPARQL

### 1. Lister tous les patients (adultes ou enfants) avec leurs symptomes 
PREFIX : <http://www.example.org/psychologie#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>

SELECT ?patient ?symptome
WHERE {
  ?patient a ?type .
  ?type rdfs:subClassOf* :Patient .
  { ?patient :aSymptome ?symptome . }
  UNION
  { ?patient :aSymptomePhysique ?symptome . }
  UNION
  { ?patient :aSymptomePsychologique ?symptome . }
}
### 2. Lister les troubles psychologiques avec les interventions recommendées
SELECT ?trouble ?intervention
WHERE {
  ?trouble a ?type .
  ?type rdfs:subClassOf* :TroublePsychologique .
  ?trouble :recommandeIntervention ?intervention .
}

### 3. Lister les tests pris par chaque patient
SELECT ?patient ?test
WHERE {
  ?patient a ?type .
  ?type rdfs:subClassOf* :Patient .
  ?patient :prendsTest ?test .
}

### 4. Lister tous les sous types de TroublePsychologique
SELECT ?subTrouble
WHERE {
  ?subTrouble rdfs:subClassOf :TroublePsychologique .
}

### 5. Lister les patients (Enfant or Adulte) giagnostiqué avec TDAH
SELECT ?patient
WHERE {
  ?patient a ?type .
  ?type rdfs:subClassOf* :Patient .
  ?patient :diagnostiqueAvec :tdah .
}
