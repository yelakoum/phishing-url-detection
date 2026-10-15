# 🎣 Détection de liens de phishing (Machine Learning)

Petit projet pédagogique : prédire si une URL est un lien de **phishing** ou un lien **légitime**, uniquement à partir du texte de l'URL.

Le notebook est écrit sous forme de **questions / réponses**, étape par étape, du chargement des données jusqu'à l'analyse des limites du modèle.

## Contenu

```
phishing-url-detection/
├── phishing_detection.ipynb   # le notebook (avec les résultats affichés)
├── data/urls.csv              # 10 000 URLs labellisées (0 = légitime, 1 = phishing)
├── requirements.txt
└── README.md
```

## Démarche

1. Exploration des données (classes équilibrées 50/50)
2. Extraction de 9 features simples : longueur de l'URL et du domaine, nombre de points, tirets, chiffres, slashs, présence de `@`, d'une adresse IP et de mots suspects (`login`, `verify`, `secure`…)
3. Entraînement d'une **régression logistique** et d'un **Random Forest** (scikit-learn)
4. Évaluation : accuracy, precision, recall, matrice de confusion, importance des features
5. Test sur des URLs réelles et analyse critique (biais des données, *distribution shift*)

## Résultats

| Modèle | Accuracy (test) |
|---|---|
| Régression logistique | ~83 % |
| Random Forest | ~96 % |

Le notebook montre aussi que le modèle se trompe sur certaines URLs réelles qui ne ressemblent pas aux données d'entraînement : une bonne note sur le jeu de test ne suffit pas.

## Lancer le projet

```bash
pip install -r requirements.txt
jupyter notebook phishing_detection.ipynb
```

## Données

- Phishing : URLs vérifiées issues de [PhishTank](https://phishtank.org/)
- Légitimes : URLs du jeu [ISCX-URL-2016](https://www.unb.ca/cic/datasets/url-2016.html) (Université du Nouveau-Brunswick) et pages d'accueil de sites populaires

Listes récupérées via le dépôt public [shreyagopal/Phishing-Website-Detection-by-Machine-Learning-Techniques](https://github.com/shreyagopal/Phishing-Website-Detection-by-Machine-Learning-Techniques) et [zer0h/top-1000000-domains](https://github.com/zer0h/top-1000000-domains), puis échantillonnées (5 000 par classe).

## Auteur

Youssef EL AKOUM — élève ingénieur ITI (Informatique, Systèmes et IA), INSA Rouen Normandie
