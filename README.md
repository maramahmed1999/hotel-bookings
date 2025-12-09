# Drive & Survive - Forest Racing Game

A 3D racing game built with Python, Pygame, and OpenGL featuring modular architecture.

## 🎮 Game Overview

Navigate through a winding forest track, avoiding obstacles and staying on the road to reach the finish line. Hit an obstacle and you lose - but stay on course and race against the clock for the best score!

---

## 📁 Module Architecture

This project follows a clean modular architecture where each module has a single, clear responsibility.

### *1. config.py* - "The Settings Manager"
*Purpose:* Centralized configuration and constants

*Contains:*
- Window dimensions and title
- All colors (car, trees, obstacles, UI)
- Physics values (speed, acceleration, friction)
- Collision radii and penalties
- World boundaries and limits
- Camera settings
- Road control points
- Generation parameters (tree count, seeds)
- Lighting values
- Scoring formulas


---

### *2. geometry.py* - "The 3D Shape Library"
*Purpose:* Low-level primitive drawing functions

*Contains:*
- draw_box() - Draws cubes/rectangles
- draw_sphere() - Draws spheres/balls
- draw_cylinder() - Draws cylinders/tubes

---

### *3. entities.py* - "The Game Objects"
*Purpose:* Interactive game entities with behavior

*Contains:*
- Car class - Player vehicle with physics, collision, rendering
- draw_tree() - Static scenery objects
- draw_obstacle() - Hazards that end the game


---

### *4. environment.py* - "The World Builder"
*Purpose:* Creates and renders the game world

*Contains:*
- smooth_curve() - Mathematical spline interpolation
- generate_road() - Creates the race track
- generate_trees() - Randomly places trees
- generate_obstacles() - Randomly places hazards
- draw_road(), draw_borders(), draw_ground() - Renders static world elements
- draw_start_line(), draw_finish_line() - Renders race markers


---

### *5. camera.py* - "The Viewpoint Controller"
*Purpose:* Manages where and how the player sees the game

*Contains:*
- setup_camera() - Positions camera based on game state
  - Following car during gameplay
  - Overview angle for menus


---

### *6. ui.py* - "The Interface Renderer"
*Purpose:* All 2D overlays and text rendering

*Contains:*
- draw_panel_2d() - Colored boxes with borders
- render_text() - Text display
- setup_2d_rendering(), restore_3d_rendering() - Mode switching
- draw_start_screen() - Main menu
- draw_playing_hud() - In-game timer
- draw_finished_screen() - Victory screen
- draw_lose_screen() - Game over screen


---

### *7. rendering.py* - "The Scene Orchestrator"
*Purpose:* Coordinates what gets drawn and when

*Contains:*
- render_world() - Calls all 3D drawing in correct order
- render_ui() - Decides which UI screen to show

---

### *8. car game.py* - "The Conductor" ⭐
*Purpose:* Main game loop - orchestrates everything

*Contains:*
- initialize_opengl() - One-time OpenGL setup
- handle_events() - Keyboard/window input
- update_game_state() - Game rules and state transitions
- main() - The game loop that ties everything together

---

## 📊 System Flow Diagram


car game.py (main loop)
    ↓
    ├─→ config.py (reads settings)
    ├─→ environment.py (generates world)
    ├─→ entities.py (creates car)
    │
    ├─→ handle_events() (input)
    ├─→ update_game_state() (logic)
    │      └─→ entities.Car.update() (physics)
    │
    ├─→ camera.py (sets viewpoint)
    ├─→ rendering.py (orchestrates drawing)
    │      ├─→ environment.py (draws world)
    │      ├─→ entities.py (draws objects)
    │      └─→ geometry.py (draws shapes)
    │
    └─→ ui.py (draws interface)


---

## 🚀 Installation & Running

### Requirements
```bash
pip install pygame PyOpenGL PyOpenGL_accelerate
```

### Run the Game

```bash
python game.py
``` 

---

## 🎯 Controls

- *UP Arrow* - Accelerate forward
- *DOWN Arrow* - Brake/reverse
- *LEFT/RIGHT Arrows* - Turn
- *SPACE* - Start game / Restart after finish
- *ESC* - Exit game

## 👩‍💻 Team Members:
- Heba Ahmed Ibrahim Agamy
- Maram Hazem Fouad Ismail Ahmed
- Menna Ahmed Ibrahim Agamy
- Mohamed Elsayed Mohamed Ahmed Aboelsoud
- Mohamed Khaled El-Daheesh Ahmed
- Mohamed Refat mostafa Abd-Elmajid Naser
- Wessam Mohammed El-Said El-Hanafy

*Happy Racing! 🏁*