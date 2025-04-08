# Ontologie pour la Santé Mentale

Ce projet a pour but de modéliser le domaine de la santé mentale en intégrant les concepts suivants :
1. **Patient**
2. **Symptômes**
3. **Troubles Psychologiques**
4. **Test**
5. **Intervention**

Les relations principales mises en place sont :
- **aSymptome** (avec sous-propriétés *Physique* et *Psychologique*)
- **diagnostiquéAvec**
- **prendsTest**
- **recommandeIntervention**

---

## Table des Matières

- [Contexte et Objectifs](#contexte-et-objectifs)
- [Modélisation du Domaine](#modélisation-du-domaine)
  - [Classes et Sous-classes](#classes-et-sous-classes)
  - [Propriétés et Sous-propriétés](#propriétés-et-sous-propriétés)
  - [Tableau récapitulatif](#tableau-récapitulatif)
- [Namespaces Utilisés](#namespaces-utilisés)
- [Exemples de Requêtes SPARQL](#exemples-de-requêtes-sparql)
- [Structure du Dépôt](#structure-du-dépôt)
- [Conclusion](#conclusion)

---

## Contexte et Objectifs

Ce projet vise à construire une ontologie détaillée pour la santé mentale en utilisant des technologies sémantiques (RDF, RDFS, OWL, SPARQL, et SWRL). L'objectif est de modéliser les interactions entre les patients, leurs symptômes, les troubles diagnostiqués, les tests de diagnostic et les interventions thérapeutiques.

---

## Modélisation du Domaine

### Classes et Sous-classes

- **Patient**
  - **Adulte**
  - **Enfant**
- **Symptômes**
- **Troubles Psychologiques**
  - **Neurodéveloppemental**
  - **De humeur**
  - **De personnalité**
- **Test**
- **Intervention**

### Propriétés et Sous-propriétés

- **aSymptome**
  - **Physique**
  - **Psychologique**
- **diagnostiquéAvec**  
  *(Lie un Patient à un Trouble Psychologique)*
- **prendsTest**  
  *(Lie un Patient à un Test)*
- **recommandeIntervention**  
  *(Lie un Trouble Psychologique à une Intervention)*

### Tableau récapitulatif

| **Catégorie**             | **Élément Général**         | **Sous-éléments / Relations**                                                                                                                                                   |
|---------------------------|-----------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Classes : Patient**     | Patient                     | - Adulte<br>- Enfant                                  |
| **Classes : Symptômes**   | Symptômes                   | (Pas de sous-classe spécifique, regroupe l'ensemble des symptômes)                                                   |
| **Classes : Troubles**    | TroublePsychologique        | - Neurodéveloppemental<br>- De humeur<br>- De personnalité |
| **Classes : Test**        | Test                        | (Représente les différents tests de diagnostic)                                 |
| **Classes : Intervention**| Intervention                | (Représente les interventions thérapeutiques)                |
| **Propriétés : aSymptome** | aSymptome                   | - Physique<br>- Psychologique                         |
| **Autres Propriétés**     | diagnostiquéAvec            | Lie un Patient à un Trouble Psychologique             |
|                           | prendsTest                  | Lie un Patient à un Test                              |
|                           | recommandeIntervention      | Lie un Trouble Psychologique à une Intervention        |

---

## Namespaces Utilisés

| Préfixe | URI                                         |
|---------|---------------------------------------------|
| `xsd`   | http://www.w3.org/2001/XMLSchema#            |
| `dc`    | http://purl.org/dc/elements/1.1/             |
| `foaf`  | http://xmlns.com/foaf/0.1/                   |
| `rdfs`  | http://www.w3.org/2000/01/rdf-schema#         |
| `owl`   | http://www.w3.org/2002/07/owl#               |
| `skos`  | http://www.w3.org/2004/02/skos/core#          |

Ces namespaces garantissent l'interopérabilité et permettent d'utiliser des vocabulaires standards pour enrichir notre ontologie.

---

## Exemples de Requêtes SPARQL

### 1. Patients adultes avec symptômes physiques

```sparql
SELECT ?patient WHERE {
  ?patient a :Adulte .
  ?patient :aSymptomePhysique ?symptome .
}
