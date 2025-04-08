# Ontologie pour la Santé Mentale

## 🎯 Domaine choisi : Santé mentale

Ce projet porte sur la modélisation des interactions entre **patients**, **symptômes**, **troubles psychologiques**, **tests** et **interventions thérapeutiques**. Il a été conçu dans le cadre d'un mini-projet visant à maîtriser les technologies sémantiques à travers RDF, RDFS, OWL, SPARQL et SWRL.

---

## 🧠 Motivation et Justification

La santé mentale est un domaine crucial qui nécessite une représentation claire et structurée des données pour permettre :
- Une meilleure compréhension des symptômes et des troubles.
- Une modélisation précise des tests de diagnostic.
- Une recommandation cohérente des interventions thérapeutiques.

Grâce à une ontologie, nous pouvons inférer de nouvelles connaissances à partir de faits simples (ex : un patient avec plusieurs symptômes peut être diagnostiqué automatiquement).

---

## 🧱 Concepts modélisés

### ✅ Classes principales

- **Patient**
- **Symptome**
- **TroublePsychologique**
- **Test**
- **Intervention**

### 🔗 Propriétés (Relations)

| Propriété              | Domaine   | Gamme               | Exemple                                         |
|------------------------|-----------|---------------------|--------------------------------------------------|
| `aSymptome`            | Patient   | Symptome            | Alice `aSymptome` insomnie                      |
| `diagnostiquéAvec`     | Patient   | TroublePsychologique| Alice `diagnostiquéAvec` dépression             |
| `recommandeIntervention`| TroublePsychologique | Intervention | Dépression `recommandeIntervention` CBT         |
| `prendsTest`           | Patient   | Test                | Alice `prendsTest` BeckDepressionInventory      |

---

## 🌐 Namespaces utilisés

| Préfixe | URI |
|--------|-----|
| `xsd`  | http://www.w3.org/2001/XMLSchema# |
| `dc`   | http://purl.org/dc/elements/1.1/ |
| `foaf` | http://xmlns.com/foaf/0.1/ |
| `rdfs` | http://www.w3.org/2000/01/rdf-schema# |
| `owl`  | http://www.w3.org/2002/07/owl# |
| `skos` | http://www.w3.org/2004/02/skos/core# |

---

## 🔍 Requêtes SPARQL

### 1. Trouver tous les symptômes d'un patient donné
```sparql
SELECT ?symptome WHERE {
  ?patient foaf:name "Alice" .
  ?patient :aSymptome ?symptome .
}
