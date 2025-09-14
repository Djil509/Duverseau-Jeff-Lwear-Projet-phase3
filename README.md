# Duverseau-Jeff-Lwear-Projet-phase3

# Project title: Prédiction de l’état des points d’eau en Tanzanie

##  Contexte
L’accès à l’eau potable est un enjeu majeur en Tanzanie.  
Ce projet vise à **prédire l’état des points d’eau (puits)** à partir de données ouvertes, afin d’aider les décideurs à mieux cibler les interventions de maintenance.

L’état d’un point d’eau peut être :
- **functional** : puits en état de fonctionnement  
- **non functional** : puits en panne  
- **functional needs repair** : puits fonctionnel mais nécessitant une réparation  

---

##  Objectifs
- Analyser les données (EDA, nettoyage, traitement des valeurs manquantes).  
- Mettre en place un pipeline de prétraitement (encodage, normalisation).  
- Tester plusieurs modèles de machine learning :  
  - Régression Logistique  
  - Arbre de Décision  
  - Random Forest  
- Comparer les performances et proposer des **recommandations business**.  

---

##  Méthodologie
1. **Prétraitement**  
   - Encodage des variables catégorielles (OneHotEncoder).  
   - Transformation des booléens en catégories.  
   - Normalisation des variables numériques.  
   - Gestion du déséquilibre de classes avec `class_weight="balanced"`.  

2. **Modélisation**  
   - Régression Logistique (baseline, balanced).  
   - Arbre de Décision (profondeur limitée pour éviter l’overfitting).  
   - Random Forest (200 arbres, balanced).  

3. **Évaluation**  
   - Accuracy, F1-score, Recall, Precision.  
   - Matrice de confusion.  
   - Visualisation des probabilités prédites.  
   - Importance des features.  

---

##  Résultats
### ⚖ Comparaison des modèles
- **Régression logistique** : robuste et performante sur les classes majoritaires, mais faible sur *needs repair*.  
- **Arbre de décision** : interprétable, mais tendance au sur-apprentissage, faible recall sur *needs repair*.  
- **Random Forest** : meilleur compromis global, meilleure détection de *non functional*, mais la classe *needs repair* reste sous-représentée.  

###  Recommandations business
1. Prioriser la réparation préventive des puits identifiés comme *non functional* ou *needs repair*.  
2. Intégrer davantage de données terrain pour améliorer la détection de la classe *needs repair*.

### Conclusion

L’analyse a montré que la régression logistique offre les meilleures performances globales pour distinguer les puits fonctionnels et non fonctionnels, tout en restant robuste et généralisable. L’arbre de décision apporte une bonne interprétabilité mais souffre de surapprentissage, tandis que la random forest améliore légèrement la précision grâce à son approche ensembliste, au prix d’une complexité plus élevée.

Dans le cadre de ce projet, nous retenons la régression logistique avec pondération des classes comme méthode principale, car elle combine une bonne performance globale, une relative simplicité de mise en œuvre et une interprétation claire des résultats.
