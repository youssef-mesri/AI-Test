# Test technique – Diffusion pour la génération de microstructures matériaux

**Durée :** à rendre sous 48h  
**Outils autorisés :** Python, PyTorch, NumPy

## Livrables

1. Un notebook ou script Python
2. Un court PDF (2 pages max) expliquant les choix méthodologiques

---

## Contexte

On considère une base de données synthétique de microstructures 2D représentées par :


- **Une image binaire** `M(x,y)` = (grains)

- **Un champ scalaire** `G(x,y)` = taille de grain locale

- **Un champ scalaire** `O(x,y)` = orientation cristallographique

- **Un vecteur global de métriques :**

$$z = (\mu_G, \sigma_G, \mu_O, \text{nb\_voisins})$$

**L'objectif** est de générer des microstructures cohérentes conditionnellement à `z`.

---

## Partie 1 — Analyse exploratoire (30 min)

Charger le dataset fourni (`.npz`) contenant `(M, G, O, z)`.

### Visualiser :

- 5 microstructures aléatoires
- Histogrammes de `G`, `O`

### Calculer :

- Les corrélations entre `z` et les statistiques spatiales

---

## Partie 2 — Diffusion conditionnelle (1h30)

On souhaite implémenter un DDPM conditionnel :

$$p_\theta(x_0 \mid z)$$

avec :

- **Entrée :** image bruitée `(x_t, t, z)`
- **Sortie :** estimation du bruit

### Tâches :

1. Implémenter un petit U-Net conditionnel
2. Encoder `z` via un MLP et l'injecter par **FiLM**
3. Entraîner sur 50 epochs

---

## Partie 3 — Évaluation physique (1h)

Pour **20 microstructures générées** :

### Recalculer :

- Taille moyenne de grain
- Distribution des orientations
- Nombre moyen de voisins

### Comparer :

- Aux valeurs conditionnelles `z`

### Tracer :

- Une courbe : erreur relative sur chaque métrique

---

## Partie 4 — Question ouverte (1h)

**Sans coder**, proposer une stratégie pour :

> Générer des microstructures 3D cohérentes à partir de métriques 2D uniquement.


---

## Notes

- Le code doit être **clair et commenté**
- Les choix méthodologiques doivent être **justifiés**
- L'évaluation doit être **quantitative et visuelle**
