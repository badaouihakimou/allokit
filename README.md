# allokit

Équations allométriques pour estimer la biomasse forestière tropicale, avec une attention particulière à l'Afrique de l'Ouest.

Tout est contenu dans un notebook autonome : **`allometrie_demo.ipynb`**. Il s'ouvre dans Google Colab ou Jupyter et se lance sans installation particulière, hormis les bibliothèques scientifiques usuelles (`numpy`, `pandas`, `matplotlib`).

## Pourquoi ce projet

Une équation allométrique convertit des mesures simples relevées sur un arbre — diamètre, hauteur, densité du bois — en une estimation de sa biomasse aérienne.

Les produits satellitaires de biomasse comme GEDI reposent sur des équations pantropicales génériques, calibrées majoritairement hors d'Afrique et appliquées partout sans distinction de type de forêt. Cela introduit un biais documenté sur le continent africain : sur des données de terrain ivoiriennes, GEDI sous-estime la biomasse des forêts denses de façon significative.

Le choix de l'équation est donc une source d'erreur de premier ordre, en amont de tout modèle de télédétection. Ce projet rassemble plusieurs équations — pantropicales et africaines — et mesure l'écart entre elles.

## Ce que montre le notebook

Le notebook démontre, chiffres à l'appui, que **le choix de l'équation change la biomasse estimée d'environ 46 % sur une forêt dense**, et que cet écart se concentre sur les gros arbres : de +7 % pour un arbre de 10 cm de diamètre à +55 % pour un arbre de 90 cm. Comme les gros arbres portent l'essentiel de la biomasse d'une forêt dense, c'est là que le choix pèse le plus.

Il contient :

- les équations, avec leurs références publiées ;
- une table de densité du bois par espèce ;
- le passage de l'arbre à la parcelle, en tonnes par hectare ;
- une comparaison des équations sur une même parcelle ;
- un graphique de divergence selon le diamètre ;
- des tests de cohérence physique que l'on peut relancer ;
- une cellule libre pour tester ses propres arbres.

## Utilisation

Ouvrir `allometrie_demo.ipynb` dans Colab (Fichier → Importer le notebook, ou glisser le fichier) et exécuter les cellules dans l'ordre. Aucune donnée externe n'est requise.

## Équations disponibles

| Équation | Région | Prédicteurs | Référence |
|---|---|---|---|
| Chave 2014 (hauteur) | pantropical | diamètre, densité, hauteur | Chave et al. 2014 |
| Chave 2014 (facteur E) | pantropical | diamètre, densité, climat | Chave et al. 2014 |
| Ngomanda 2014 | Afrique centrale (Gabon) | diamètre, hauteur | Ngomanda et al. 2014 |
| Aabeyir 2020 | Afrique de l'Ouest (Ghana) | diamètre, densité, hauteur | Aabeyir et al. 2020 |

## Ce que le notebook établit

L'écart entre équations n'oppose pas « africain » à « pantropical » : les équations de Chave (pantropicale) et d'Aabeyir (Ghana) donnent des valeurs proches, tandis que celle de Ngomanda (forêt humide du Gabon) prédit plus lourd. Ce qui compte est le **type de forêt** sur lequel l'équation a été calibrée.

Conséquence : corriger la cible en amont, avec une équation adaptée au milieu, est un levier au moins aussi important que le choix du capteur ou du modèle dans un projet de cartographie de biomasse.

## Limites

- Les coefficients régionaux sont repris de la littérature ; les vérifier contre les publications d'origine avant tout usage critique.
- La biomasse souterraine n'est pas estimée.
- La table de densité du bois est minimale ; la remplacer par la Global Wood Density Database (Zanne et al. 2009) pour un usage réel.
- Chaque équation a un domaine de validité (plage de diamètre, type forestier) qu'il faut respecter.

## Références

- Chave J. et al. (2014). *Improved allometric models to estimate the aboveground biomass of tropical trees.* Global Change Biology. doi:10.1111/gcb.12629
- Chave J. et al. (2005). *Tree allometry and improved estimation of carbon stocks and balance in tropical forests.* Oecologia 145:87-99.
- Ngomanda A. et al. (2014). *Site-specific versus pantropical allometric equations: Which option to estimate the biomass of a moist central African forest?* Forest Ecology and Management.
- Aabeyir R. et al. (2020). *Allometric models for estimating aboveground biomass in the tropical woodlands of Ghana.* Forest Ecosystems. doi:10.1186/s40663-020-00250-3
- Zanne A.E. et al. (2009). *Global Wood Density Database.*

## Licence

MIT.
