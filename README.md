# FPS Retro Doom Game
 
A retro-style first-person shooter built in Python using Pygame, inspired by classic 90s FPS games like Doom and Wolfenstein 3D. The game uses raycasting to simulate a 3D environment from a 2D map — the same technique used in the original Doom engine.
 
> **Work in Progress** — This project is actively being developed. Features and structure may change.

 ---
 
## Built With
 
- **Python 3.12**
- **Pygame 2.6**
 
---

##  Project Structure
 
```
FPS-Retro-Doom-Game/
│
├── main.py              # Entry point — initialises the game loop
├── settings.py          # Global constants (screen size, FOV, texture size, etc.)
├── map.py               # Map layout and world grid
├── player.py            # Player movement, rotation, and position
├── raycasting.py        # Raycasting engine — handles 3D projection
├── object_renderer.py   # Renders walls and textured surfaces
├── sprite_object.py     # Static and animated sprite objects
│
└── resources/
    └── textures/        # Wall texture files (1.png – 5.png)
```
 
--- 

## How It Works
 
The game uses a **raycasting algorithm** to project a 2D grid map into a pseudo-3D view:
 
1. **Map** — A 2D grid defines the world. Each cell value (1–5) maps to a wall texture, and `0` represents empty space.
2. **Raycasting** — For each vertical screen column, a ray is cast from the player's position. The distance to the nearest wall is used to calculate the projected wall height.
3. **Object Renderer** — Wall columns are sliced from the appropriate texture and scaled based on depth, then drawn to the screen.
4. **Player** — Moves and rotates in the 2D map space, with a configurable FOV and movement speed.
5. **Fisheye Correction** — Applied to remove the distortion caused by straight-line raycasting.

 ---
  
## Map Format
 
The map is defined as a 2D list in `map.py`. Each value represents:
 
| Value | Meaning |
|-------|---------|
| `0` | Empty space (walkable) |
| `1–5` | Wall with corresponding texture |
 
Example:
```python
mini_map = [
    [1, 1, 1, 1, 1],
    [1, 0, 0, 0, 1],
    [1, 0, 2, 0, 1],
    [1, 0, 0, 0, 1],
    [1, 1, 1, 1, 1],
]
```
 
---
 
## Configuration
 
All global settings are in `settings.py`:
 
```python
# Screen
WIDTH, HEIGHT = 1600, 900
FPS = 60
 
# Player
PLAYER_SPEED = 0.004
PLAYER_ROT_SPEED = 0.002
FOV = math.pi / 3  # 60 degrees
 
# Raycasting
NUM_RAYS = WIDTH // 2
MAX_DEPTH = 20
 
# Textures
TEXTURE_SIZE = 256
SCALE = WIDTH // NUM_RAYS
```
 
---
 
## Textures
 
Wall textures are stored in `resources/textures/` and named `1.png` through `5.png`, matching the map cell values. Textures must be square images — the default resolution is `256x256`.

All textures were downloaded from https://spritedatabase.net
 
---

## Roadmap
 
- [x] Raycasting engine
- [x] Textured wall
- [x] 3D Projection
- [x] Player movement and rotation
- [x] Texturing the level
- [ ] Sprite objects
- [ ] Weapons
- [ ] Enemies with AI
- [ ] Collision detection improvements
- [ ] Minimap HUD
- [ ] Sound effects and music
- [ ] Interactive Gameplay
