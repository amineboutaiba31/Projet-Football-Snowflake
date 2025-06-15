# Projet-Football-Snowflake
# 📘 Documentation – Projet Football Snowflake

## 🎯 Objectif du projet

Créer un système complet de gestion et d’analyse du championnat de football anglais (Premier League) sur Snowflake, avec intégration de Python pour l’ELT et Power BI pour la visualisation.

---

## 🧱 Architecture de la base de données (Snowflake)

### 🗂️ Schéma : `premier_league`

### 🧾 Tables principales :

* `federation`
* `stade`
* `equipe`
* `joueur`
* `arbitre`
* `calendrier`
* `match`
* `statistiques_match`
* `but`
* `classement`

---

## ⚙️ Étapes réalisées

### 1. **Création des tables** avec relations (clé étrangère, contraintes)

### 2. **Remplissage des tables** avec des données réalistes (20 clubs, joueurs, stades, matchs, etc.)

### 3. **Ajout de données incorrectes dans les CSV** pour simuler des cas d’ELT (nulls, doublons, incohérences)

### 4. **Traitement ETL avec Snowpark Python**

* Chargement du fichier CSV des joueurs « sales »
* Détection des erreurs :

  * Valeurs nulles
  * Doublons
  * `equipe_id` invalide
* Export vers fichiers `CSV` d’erreurs pour analyse

### 5. **Automatisation des résultats**

* Création d’une **procédure `inserer_resultat_auto()`** (résultats simulés automatiquement)
* Création d’une **tâche planifiée (TASK)** qui s’exécute toutes les 2 minutes

### 6. **Mise à jour du classement**

* Une procédure `mettre_a_jour_classement()` qui recalcule le classement selon les résultats (à venir automatiser dans une tâche planifiée)

### 7. **Sécurité et gestion des accès (rôles)**

* Définition des rôles utilisateurs et attribution des droits :

  * `role_arbitre` : insérer/modifier les résultats de match et classement
  * `role_federation` : gérer le calendrier, les statistiques, les classements
  * `role_president` : insérer, modifier, supprimer les équipes
  * `role_entraineur` & `role_joueur` : lecture seule sur toutes les tables
* Création des utilisateurs dans Snowflake avec login/mot de passe dédiés
* Connexion à Snowflake avec rôles personnalisés pour chaque profil
* Vérification des privilèges et de la sécurité des accès

---

## 📊 Power BI – Visualisation (à faire)

Préparation des dashboards :

* 🔢 Classement des équipes par saison
* ⚽ Meilleurs buteurs
* 📈 Statistiques par match : tirs, possessions, fautes
* 🏟️ Analyse de performances domicile/extérieur

---

## 🔮 Étapes futures

### 1. **Modélisation prédictive des résultats de match**

* Utilisation des saisons précédentes
* Features : statistiques, historique, home/away, joueurs
* Modèles envisagés :

  * Régression logistique
  * Random Forest
  * XGBoost

### 2. **Ajout de nouveaux dashboards Power BI**

* Courbe d’évolution du classement par journée
* Corrélations entre stats et résultats
* Tableaux croisés dynamiques sur les joueurs et les clubs

---

## ✅ Conclusion

Projet avancé combinant :

* Modélisation relationnelle Snowflake
* Sécurité multi-rôles avec utilisateurs dédiés
* Automatisation (TASK + PROCEDURE)
* Python pour la qualité des données
* Visualisation interactive avec Power BI

> Prochaines étapes : intégrer l’intelligence artificielle pour la prédiction des matchs, enrichir les tableaux de bord Power BI, et automatiser la mise à jour du classement après chaque match.
