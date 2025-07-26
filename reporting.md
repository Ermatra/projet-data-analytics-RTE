# Rapport d'Analyse des Données du Réseau Électrique RTE

**Objectif :** Évaluer la stabilité, l'efficacité et les comportements du réseau HTA/BT en France à partir des mesures issues des postes.

---

## 1. Résumé Exécutif

L’analyse couvre les performances du réseau électrique de RTE sur une journée complète. Les métriques étudiées révèlent un réseau majoritairement stable, efficace et bien équilibré géographiquement. Les principaux enseignements :

- **Stabilité du réseau :** 98 % des mesures indiquent un état normal (0).
- **Efficacité énergétique :** cos_phi ≥ 0.999 pour 74 % des cas ; 18 % à 1.000.
- **Cycle quotidien clair :** courbes sinusoïdales pour consommation/production.
- **Transformateurs :** puissances actives et réactives stables ; pics d’intensité sur T1_I_A et T2_I_A.
- **Homogénéité géographique :** aucune disparité significative entre les zones.
- **États d’alerte rares :** aucun impact significatif détecté sur les moyennes globales.

---

## 2. Méthodologie

### 2.1 Données

- **Nombre d’observations :** 1440 (résolution : 1 minute)

- **Variables continues :**  
  `timestamp`, `consommation_MW`, `production_MW`, `Q_total_MVAR`, `S_total_MVA`,  
  `cos_phi`, `frequence_Hz`, `T1_P_MW`, `T1_Q_MVAR`, `T1_I_A`,  
  `T2_P_MW`, `T2_Q_MVAR`, `T2_I_A`.

- **Variables discrètes :**  
  `etat_reseau`, `nb_lignes_HT`, `zone_reseau`, `jour_type`.

### 2.2 Techniques utilisées

- **Univariée :** histogrammes, boxplots, barplots, stats descriptives.  
- **Multivariée :**
  - Discrète/Discrète : tables de contingence + test du Chi-2.
  - Continue/Continue : scatter plots, corrélations.
  - Discrète/Continue : moyennes par groupe, test de Kruskal-Wallis.

---

## 3. Analyse Détaillée

### 3.1 Analyse Univariée

- **cos_phi :**  
  Distribution très concentrée autour de 0.999 (74 %) et 1.000 (18 %) → excellente compensation réactive.

- **etat_reseau :**  
  État 0 (normal) dans 98 % des cas.

- **nb_lignes_HT :**  
  4 lignes (32 %) > 3 (28 %) > 5 (21 %) > 2 (19 %).

- **zone_reseau :**  
  Répartition homogène entre Nord, Sud, Est, Ouest, Centre.

- **jour_type :**  
  Un jour ouvré.

- **timestamp :**  
  22/07/2025, de 00:00 à 23:59.

- **consommation_MW & production_MW :**  
  Moyenne ≈ 50 000 MW ; écarts-types ≈ 5 700 MW.  
  Courbes sinusoïdales → comportement journalier typique.

- **frequence_Hz :**  
  Moyenne : 49.998 Hz, écart-type très faible → stabilité remarquable.

- **Transformateurs T1/T2 :**
  - T1_P_MW ≈ 198.8 MW ; T2_P_MW ≈ 179.45 MW.
  - Q_MVAR ≈ 50 MVAR / 45 MVAR.
  - I_A ≈ 504 A, mais avec outliers notables (jusqu’à 1129 A).

- **Q_total_MVAR & S_total_MVA :**  
  Moyennes ≈ 1992 MVAR et 50130 MVA → cohérence avec un réseau haute tension.

---

### 3.2 Analyse Multivariée

#### 3.2.1 Discrète / Discrète

- **cos_phi vs etat_reseau :**  
  Le cos_phi élevé (≥ 0.999) est très fortement associé à un état réseau normal.  
  **Test Chi-2 :** p < 0.0001 → relation significative.

- **cos_phi vs zone_reseau :**  
  Aucune disparité entre zones → compensation uniforme sur tout le territoire.

#### 3.2.2 Continue / Continue

- **Évolution temporelle :**
  - `consommation_MW` & `production_MW` : cycles clairs, synchronisés.
  - `S_total_MVA` suit une tendance similaire.
  - `T2_I_A` : forte variabilité sans tendance.

- **Corrélations notables :**
  - `production_MW` vs `consommation_MW` → linéarité forte.
  - `S_total_MVA` vs `consommation_MW`/`production_MW` → corrélation élevée.
  - `T2_P_MW` vs `T2_I_A` → corrélation physique logique.

#### 3.2.3 Discrète / Continue

- **cos_phi vs variables continues :**
  - Consommation & production augmentent avec cos_phi → meilleur rendement énergétique.
  - `Q_total_MVAR` diminue avec cos_phi → meilleure compensation.
  - `T1_P_MW` & `T2_P_MW` : stables.
  - `T2_I_A` : légère baisse avec cos_phi.

- **etat_reseau vs variables continues :**
  - Moyennes globalement similaires entre états 0/1/2.
  - **Kruskal-Wallis :** pas de différence significative → peu de données pour états 1/2.

- **zone_reseau vs variables continues :**
  - Aucune différence significative entre les zones.

---

## 4. Recommandations

- ✅ **Maintenir un cos_phi élevé**  
  - Maximiser l'efficacité énergétique.  
  - Réduire la puissance réactive.  
  - Assurer une surveillance continue du système de compensation.

- ⚠️ **Surveiller les pics d’intensité (T1_I_A, T2_I_A)**  
  - Risque d’échauffement ou de surcharge locale.  
  - Analyser les contextes d’apparition (heure, zone, activité).

- 📉 **États d’alerte (1 et 2)**  
  - Trop rares pour conclure.  
  - Recommandation : enrichir la base de données, mieux capter ces états.

- 🔍 **Vérifier l’indépendance fonctionnelle des transformateurs**  
  - Faible corrélation entre T1/T2 et conso/production globale → possible logique de découplage fonctionnel.  
  - À creuser avec documentation réseau et ingénierie terrain.

- 🌍 **Homogénéité géographique**  
  - Permet de transposer les bonnes pratiques d’une zone à l’autre.  
  - Gage de résilience réseau.

---

## 5. Conclusion

L’analyse des données de RTE sur une journée révèle un réseau stable, bien équilibré, optimisé sur le plan énergétique et sans déséquilibres géographiques marqués. L’efficacité du facteur de puissance est un levier central pour maintenir cette stabilité. Des axes d’amélioration existent autour de la gestion des outliers (pics d’intensité) et la compréhension des rares états critiques.

