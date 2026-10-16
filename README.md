# cub3D

**Un moteur de rendu 3D en raycasting**, façon Wolfenstein 3D : à partir d'une
carte 2D en texte, le monde est projeté en vue première personne avec murs
texturés, sol/plafond colorés et déplacement fluide. Écrit en C avec MiniLibX.
Projet du tronc commun de l'École 42.

![C](https://img.shields.io/badge/C-00599C?style=flat-square&logo=c&logoColor=white)
![MiniLibX](https://img.shields.io/badge/MiniLibX-X11-1a1a1a?style=flat-square)
![License](https://img.shields.io/badge/license-MIT-1a1a1a?style=flat-square)

<!-- CAPTURE À FOURNIR : déposer une image/GIF du gameplay ici, ex. docs/gameplay.png -->
<!-- puis remplacer la ligne ci-dessous :                                            -->
<!-- ![Gameplay](docs/gameplay.png)                                                  -->
> 🎥 _Capture de gameplay à venir._

## Fonctionnalités

- **Raycasting** temps réel : murs texturés selon l'orientation (`NO` `SO` `WE` `EA`).
- Couleurs de **sol et plafond** paramétrables (`F` / `C`).
- **Déplacement** : `W` `A` `S` `D`, rotation à la flèche gauche/droite.
- Sortie propre : touche `Échap` et bouton fenêtre.
- **Bonus** : minimap, et plusieurs cartes de démonstration.

## Format de carte (`.cub`)

```
NO textures/wood.xpm      # textures des 4 orientations de mur
SO textures/colorstone.xpm
WE textures/colorstone.xpm
EA textures/colorstone.xpm
F 90,90,90                # couleur du sol (RGB)
C 0,0,0                   # couleur du plafond (RGB)

111111
100N01                    # 1 = mur, 0 = vide, N/S/E/W = joueur + orientation
111111
```

Cartes prêtes à l'emploi dans [`maps/`](maps/) (`official.cub`, `big.cub`,
`circle.cub`, `giga.cub`…).

## Build & lancement

Prérequis (Linux) : `cc`, `make`, et les libs X11 — `sudo apt install libx11-dev libxext-dev`.

```bash
make                       # compile -> ./cub3D (MiniLibX inclus dans mlx/)
./cub3D maps/official.cub

make bonus                 # version bonus (minimap)
./cub3D_bonus maps/official.cub
```

## Structure

```
srcs/          parsing de la carte, raycasting, rendu, hooks clavier
includes/      en-têtes
libft/         libft maison
mlx/           MiniLibX (lib graphique)
maps/          cartes .cub de démonstration
textures/      textures murales (.xpm)
```

Compilé avec `-Wall -Wextra -Werror` (norme 42).

## Licence

MIT — voir [LICENSE](LICENSE).
