# 📊 Projet d’Analyse du Réseau Électrique RTE

## 📌 Description

Ce projet propose une analyse exploratoire et statistique approfondie des données du réseau haute tension HTA/BT en  (RTE), collectées sur une journée complète avec une résolution d'une minute. Il vise à évaluer la stabilité du réseau, l’efficacité énergétique (via le facteur de puissance), les performances des transformateurs, et l’homogénéité géographique du système.

L’analyse s’appuie sur des visualisations claires, des statistiques descriptives robustes, et des tests statistiques adaptés (Chi², Kruskal-Wallis), permettant de tirer des conclusions pertinentes et actionnables sur le comportement du réseau.

---

## 🧠 Objectifs

- Étudier le comportement journalier de la consommation et de la production électrique.
- Évaluer l’efficacité énergétique via le facteur de puissance (cos_phi).
- Analyser les performances des transformateurs (T1 et T2).
- Vérifier l’impact des états d’alerte du réseau.
- Identifier d’éventuelles disparités régionales.

---

## 🛠️ Stack Technique

- **Langage** : Python 3
- **Librairies** :
  - `pandas`, `numpy` – manipulation de données
  - `matplotlib`, `seaborn` – visualisation
  - `scipy.stats`, `statsmodels` – tests statistiques
  - `jupyter` – environnement d’analyse interactif

---

## 📂 Contenu du Projet

- `projet_data_analytics_RTE.ipynb` : notebook principal avec toute l’analyse.
- `PY-projet_data_analytics_rte.py` : version script Python du notebook.
- `rapport_RTE.md` : rapport structuré de l’analyse.
- `README.md` : ce fichier de présentation.

---

## 🔍 Principaux Résultats

- **Stabilité du réseau** : 98 % des observations en état normal.
- **Efficacité énergétique** : cos_phi ≥ 0.999 dans 92 % des cas.
- **Cycle journalier** classique de consommation/production.
- **Homogénéité géographique** : aucune disparité notable entre zones.
- **Test Chi²** : corrélation significative entre cos_phi et l’état du réseau.
- **Test de Kruskal-Wallis** : pas de variation significative selon l’état ou la zone du réseau.

---

## 👩🏽‍💼 À propos de l’Auteure

**Arame Traore**  
Ingénieure diplômée en Génie Électrique de l’INSA de Strasbourg  
Passionnée par la stabilité des réseaux, l’efficacité énergétique et la valorisation des données électriques.

📧 arame.traore6@outlook.fr  
💼 *Feel free to reach out for collaboration opportunities or professional discussions!*

---

## ✅ Recommandations

- Maintenir un **facteur de puissance élevé** pour optimiser la stabilité.
- Surveiller les **pics d’intensité** ponctuels détectés sur T1/T2.
- Enrichir les jeux de données sur les **états d’alerte** pour analyses prédictives futures.

---

## 📈 Perspective

Intégration de modèles de détection d’anomalies en temps réel sur la base de ces variables, pour améliorer la réactivité et la maintenance proactive du réseau.

---

## Licence
MIT license.
