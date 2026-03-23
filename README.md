# ✈️ Pipeline de données aviation – Airflow, Docker & BigQuery

## 📌 Présentation du projet

Ce projet met en place un **pipeline de données complet (ETL)** appliqué au domaine de l’aviation.

Il s’appuie sur le dataset **Flight Price Prediction Dataset**, une base de données permettant d’analyser et de prédire les prix des billets d’avion. Ce dataset contient notamment :

* Les compagnies aériennes
* Les villes de départ et d’arrivée
* Les routes aériennes
* Les horaires de départ et d’arrivée
* La durée des vols
* Le nombre d’escales
* Le prix des billets

L’objectif est d’automatiser le traitement de ces données afin de les rendre exploitables pour l’analyse ou le machine learning.

---

## ⚙️ Stack technique

* **Python (Pandas)** → traitement des données
* **Apache Airflow** → orchestration du pipeline
* **Docker** → environnement reproductible
* **Google BigQuery** → stockage des données (data warehouse)

---

## 🧠 Architecture du pipeline

Le pipeline suit une logique classique **ETL (Extract – Transform – Load)** :

### 🔹 Extract

* Récupère automatiquement le **fichier CSV le plus récent**
* Permet d’intégrer facilement de nouvelles données

### 🔹 Transform

* Nettoyage des données
* Transformation des dates et heures
* Conversion de la durée en format exploitable
* Encodage de variables (ex : nombre d’escales)

### 🔹 Load

* Envoi des données vers **BigQuery**
* Mise à disposition pour analyse ou reporting

---

## 🔄 Automatisation avec Airflow

Le pipeline est orchestré avec Airflow via un DAG :

* Nom du DAG : `aviation_pipeline`
* Fréquence : **hebdomadaire**
* Étapes :

  * `extract`
  * `transform`
  * `load`

---

## 🐳 Lancement avec Docker

Le projet est entièrement conteneurisé.

### ▶️ Lancer le projet

```bash
docker-compose up --build
```

Puis accéder à Airflow :

```text
http://localhost:8080
```

---

## 🔐 Authentification BigQuery

Le projet utilise les **Application Default Credentials (ADC)**.

### authentification

```bash
gcloud auth application-default login
```

## 📁 Structure du projet

```
├── dags/
│   └── pipeline.py
├── scripts/
│   ├── extract.py
│   ├── transform.py
│   └── load.py
├── data/
├── docker-compose.yml
├── Dockerfile
├── requirements.txt
```

---

## 🎯 Objectifs du projet

Ce projet permet de démontrer :

* La mise en place d’un **pipeline de données automatisé**
* L’utilisation d’outils modernes de data engineering
* Le traitement de données réelles du secteur aérien
* L’intégration avec un **data warehouse cloud (BigQuery)**
