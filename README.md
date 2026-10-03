# Prédiction du cumul pluviométrique annuel — Ouagadougou

## Contexte
Projet exploratoire visant à prédire le cumul pluviométrique annuel 
à Ouagadougou (Burkina Faso) à partir de données climatiques historiques,
dans le cadre d'un apprentissage autodidacte en data science.

## Source des données
Données journalières (précipitations, température) de 2000 à 2024,
récupérées via l'API NASA POWER (power.larc.nasa.gov) pour les 
coordonnées de Ouagadougou (12.37°N, -1.52°W).

## Méthodologie
1. Récupération des données via l'API NASA POWER
2. Nettoyage et typage (dates, valeurs numériques)
3. Analyse exploratoire (EDA) : tendance interannuelle, saisonnalité mensuelle, relation précipitation/température
4. Modélisation : régression linéaire et Random Forest pour prédire 
   le cumul de l'année N+1 à partir du cumul et de la température de l'année N

## Résultats

| Modèle | MAE (mm) | R² |
| Régression linéaire | 104 | 0,086 |
| Random Forest | 131 | -0,428 |

## Conclusion
Aucun des deux modèles n'atteint une performance exploitable. Avec seulement
24 observations annuelles et deux features simples, le problème est mal posé :
la pluviométrie sahélienne dépend de facteurs climatiques globaux 
(ex : oscillations ENSO) absents de ce jeu de données local. 

Ce résultat illustre une limite réelle et documentée de la prévision 
climatique saisonnière à partir de données locales seules.

## Pistes d'amélioration
- Intégrer des indices climatiques globaux (ENSO, SST Atlantique)
- Utiliser des données mensuelles plutôt qu'annuelles (plus d'observations)
- Explorer des modèles de séries temporelles dédiés (ARIMA, Prophet)

## Structure du dépôt
- `notebook.ipynb` : analyse complète
- `requirements.txt` : dépendances
- `README.md` : ce fichier

## Installation
\`\`\`bash
pip install -r requirements.txt
\`\`\`