# -tp_olist_KEITA_ALFA_AMADOU

# 📊 Analyse de l'E-Commerce Brésilien — Dataset Olist

> Travaux Pratiques — Module *Analyse et Traitement de Données*
> Université Kofi Annan de Guinée — Faculté des Sciences et Technologies de l'Information
> Licence 3 / Master 1 MIAGE & Génie Logiciel — Année universitaire 2025-2026

---

## 🎯 Contexte du projet

**Olist** est une marketplace brésilienne qui connecte de petits marchands à de grands canaux de vente en ligne. Ce projet analyse environ **100 000 commandes** passées entre 2016 et 2018, dans le but d'identifier des leviers d'optimisation business (délais de livraison, satisfaction client, performance par catégorie) et de formuler des recommandations concrètes à l'équipe produit d'Olist.

---

## 📁 Structure du projet

```
olist_analysis/
├── data/
│   ├── raw/                  ← 8 fichiers CSV originaux (non versionnés)
│   └── processed/            ← Données nettoyées et fusionnées
├── notebooks/
│   └── tp_olist_NOM_PRENOM.ipynb
├── visuals/                  ← Graphiques exportés (PNG, 150 dpi)
├── README.md
└── .gitignore
```

---

## 📦 Données utilisées

Le dataset est composé de **8 fichiers CSV** organisés comme une base relationnelle :

| Fichier | Contenu |
|---|---|
| `olist_orders_dataset.csv` | Commandes (statut, dates) |
| `olist_order_items_dataset.csv` | Articles commandés (prix, frais de port) |
| `olist_products_dataset.csv` | Produits (catégorie, poids) |
| `olist_customers_dataset.csv` | Clients (ville, état) |
| `olist_order_reviews_dataset.csv` | Avis clients (note 1-5) |
| `olist_sellers_dataset.csv` | Vendeurs (ville, état) |
| `olist_order_payments_dataset.csv` | Paiements (type, montant) |
| `product_category_name_translation.csv` | Traduction des catégories PT → EN |

**Source** : [Kaggle — Brazilian E-Commerce Public Dataset by Olist](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce)

---

## 🛠 Stack technique

- **Python 3**
- **Pandas** — manipulation de données
- **NumPy** — calculs numériques
- **Matplotlib** & **Seaborn** — visualisations
- **Jupyter Notebook**

---

## 🚀 Lancer le projet

### 1. Cloner le repo
```bash
git clone https://github.com/<TON_USERNAME>/<NOM_DU_REPO>.git
cd <NOM_DU_REPO>
```

### 2. Installer les dépendances
```bash
pip install pandas numpy matplotlib seaborn jupyter
```

### 3. Télécharger les données
Télécharger les 8 fichiers CSV depuis [Kaggle](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce) et les placer dans `data/raw/`.

### 4. Lancer le notebook
```bash
cd notebooks
jupyter notebook tp_olist_NOM_PRENOM.ipynb
```

Puis exécuter `Kernel → Restart & Run All Cells`.

---

## 📋 Plan de l'analyse

### **Partie 1 — Chargement & Exploration**
- Import des 8 tables CSV
- Analyse des dimensions et des types
- Détection des valeurs manquantes
- Statistiques descriptives

### **Partie 2 — Nettoyage & Feature Engineering**
- Suppression des colonnes inutiles
- Conversion des colonnes temporelles en `datetime64`
- Calcul des **délais de livraison** (`delivery_days`, `delay_days`)
- Fusion des 8 tables en un DataFrame analytique unique

### **Partie 3 — Analyse Descriptive**
- Évolution mensuelle du CA
- Top 10 des catégories par CA et par volume
- Délais de livraison par état brésilien
- Lien entre délai et satisfaction client

### **Partie 4 — Visualisations Avancées**
- Matrice de corrélation des variables clés
- Distribution des prix (avant/après filtrage P95)
- Analyse libre : modes de paiement
- Synthèse et recommandations business

### **Partie 5 — Export**
- Export du DataFrame nettoyé en CSV (`olist_df_processed.csv`)

---

## 🔑 Principaux résultats

1. **Le délai de livraison est le facteur clé de la satisfaction client.**
   Les commandes livrées en plus de 21 jours obtiennent une note moyenne de **2.7/5**, contre **4.3/5** pour celles livrées en moins de 7 jours.

2. **Forte inégalité géographique.**
   Les états du nord (Roraima, Amapá) attendent jusqu'à **28 jours** en moyenne, tandis que **São Paulo** reçoit ses commandes en **8 jours**. La logistique est concentrée dans le sud-est du Brésil.

3. **Champions en CA ≠ champions en volume.**
   `health_beauty` domine le chiffre d'affaires, mais `bed_bath_table` domine en nombre de ventes. Les catégories à prix unitaire élevé (`watches_gifts`) génèrent beaucoup de CA avec peu de ventes.

---

## 💡 Recommandations à Olist

1. **Investir dans la logistique vers le nord du Brésil** — ouvrir des entrepôts régionaux à Manaus (AM) ou Belém (PA) pour réduire les délais de moitié dans la région Nord et remonter la satisfaction client.

2. **Mettre en avant les catégories à forte rentabilité** — promouvoir les catégories à prix unitaire élevé (`watches_gifts`, `computers_accessories`) qui génèrent beaucoup de revenu avec un volume modéré, donc moins de pression logistique.

---

## 📸 Aperçu des visualisations

| Graphique | Insight clé |
|---|---|
| `ca_mensuel.png` | Pic de CA en novembre 2017 (Black Friday brésilien) |
| `top10_categories_ca.png` | `health_beauty` en tête du CA |
| `delai_par_etat.png` | Écart de 20 jours entre nord et sud-est |
| `satisfaction_vs_delai.png` | Corrélation négative claire |
| `heatmap_correlation.png` | Corrélation `delivery_days ↔ review_score` = -0.32 |
| `distribution_prix.png` | Distribution fortement asymétrique à droite |
| `analyse_paiements.png` | 75% des paiements par carte de crédit |
| `boxplot_prix.png` | Nombreuses valeurs aberrantes (jusqu'à 6735 BRL) |

---

## 👤 Auteur

**[TON_NOM_PRENOM]**
Étudiant·e en L3 / M1 MIAGE & Génie Logiciel
Université Kofi Annan de Guinée

📧 [ton.email@exemple.com](mailto:ton.email@exemple.com)

---

## 📚 Encadrant

**Almamy Camara** — Data Analyst | Data Scientist | Data Engineer

---

## 📄 Licence

Projet académique réalisé dans le cadre d'un TP universitaire. Les données proviennent du dataset public Olist sur Kaggle.