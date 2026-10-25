# Projet Pengo
Vidéo de démonstration : https://youtu.be/L0TqmwFEOVk

Ce projet implémente une version du jeu **Pengo** en Java, avec un moteur générique, un modèle de jeu, une vue avec viewport, des sprites, des collisions et des automates/bots GAL pour les ennemis.

Projet réalisé en équipe de 6 étudiants dans le cadre du Projet Logiciel en Équipe (PLE) de l'Université Grenoble Alpes. Le framework graphique `ws/given.jar` a été fourni par l'équipe pédagogique.

## 1. Compilation et lancement

Prérequis : un JDK.

Depuis le dossier `ws` :

```bash
cd ws
javac -d bin -cp given.jar $(find Pengo -name '*.java' -not -path '*/tests/*')
java -ea -cp "bin:given.jar" pengo.PengoMain
```

Le jeu doit être lancé depuis `ws/` pour trouver les ressources dans `ws/Asset/`.

## 2. Choix de la carte

Au lancement, le jeu affiche un menu de sélection de carte.

Cartes disponibles :

```text
Classic
Torus
Big ViewPort
```

Contrôles du menu :

| Touche        | Action                   |
|-------------- |--------------------------|
| Flèche haut/Z | Monter dans le menu      |
| Flèche bas /S | Descendre dans le menu   |
| Entrée        | Valider la carte choisie |


Après validation, la carte sélectionnée est chargée depuis le dossier :

```text
ws/Asset/rsrc/maps/
```

## 3. Contrôles pendant le jeu

| Touche            | Action                     |
|-------------------|----------------------------|
| Flèche haut / Z   | Aller vers le haut         |
| Flèche bas / S    | Aller vers le bas          |
| Flèche gauche / Q | Aller vers la gauche       |
| Flèche droite / D | Aller vers la droite       |
| Espace            |casser le bloc devant Pengo |
| Échap             | Ouvrir le menu pause       |


## 4. Menu pause / victoire / game over

Pendant le jeu, appuyer sur :

```text
Échap
```

ouvre le menu.

Options possibles :

```text
Reprendre
Recommencer
Quitter
```

Contrôles du menu :

| Touche          | Action                  |
|-----------------|-------------------------|
| Flèche haut / Z | Monter                  |
| Flèche bas / S  | Descendre               |
| Entrée / Espace | Valider                 |
| Q               | Quitter                 |
| R               | Recommencer directement |

## 5. Objectif du jeu

Le joueur contrôle Pengo. Le but est de survivre, d'éliminer les ennemis et d'utiliser les blocs de glace.

Fonctionnalités principales :

- Pousser des blocs de glace.
- Écraser les ennemis avec un bloc glissant.
- Casser les blocs abîmés.
- Traverser un bloc très abîmé avec ralentissement.
- Utiliser les bonus.
- Gagner avec l'alignement des DiamondBlocks ou si tous les ennemis sont morts.

## 6. Organisation générale du projet

```text
engine/      moteur générique du jeu
geometry/    grille, coordonnées et vecteurs
collision/   formes et tests de collision
model/       entités et modèle générique
gal/         actions, conditions et automates GAL
pengo/       logique spécifique au jeu Pengo
view/        affichage, viewport, avatars et overlays
Asset/       cartes, sprites et configuration
```

## 7. Remarque importante

Le moteur reste générique : il ne connaît pas les règles spécifiques de Pengo. La logique du jeu Pengo est placée dans le package :

```text
pengo
```

Cela permet de séparer clairement le moteur général, le modèle du jeu, les collisions, les automates et l'affichage.
