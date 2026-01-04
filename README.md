# The Curse of Theron — Castlevania Game Style

A run-and-gun action game inspired by classic Castlevania aesthetics, written in C using the Allegro 5 library.

## Description

The Curse of Theron blends fast-paced run-and-gun combat with gothic visuals and multi-stage boss encounters. This project demonstrates a compact game architecture in C, including resource management, sprite animation, physics, enemy AI, projectile handling, and a bilingual menu system (Portuguese and English).

## Features

- Run-and-gun action with exploration and boss fights
- Sprite-sheet animation system and camera management
- Projectile mechanics supporting multiple bullets via a linked list
- Multi-stage boss with distinct attack states (projectile and area attacks)
- Adjustable difficulty (Easy, Medium, Hard) and life modes (Normal, Double Life, HitKill)
- Vertical shooting (hero can shoot upwards)
- Objective-based progression: the boss unlocks after defeating a required number of enemies
- Bilingual menu (Portuguese / English)
- Settings for music volume and difficulty

## Technologies

- Language: C
- Game library: Allegro 5
- Assets: sprites, backgrounds, audio (.ogg)

## Requirements

- C compiler (gcc or clang)
- Allegro 5 development libraries (core, image, audio, font, ttf, primitives, mixer as needed)
- Standard build tools (make, pkg-config)

On Debian/Ubuntu example:

    sudo apt install liballegro5-dev liballegro-image5-dev liballegro-audio5-dev liballegro-font5-dev liballegro-ttf5-dev liballegro-primitives5-dev pkg-config build-essential

Adjust the commands for your OS or package manager.

## Build and run

This project provides a Makefile with the following commands:

- make          # build the game
- make run      # build (if needed) and run the game
- make clean    # remove build artifacts

Example manual build (adjust source files as necessary):

    gcc `pkg-config --cflags --libs allegro-5 allegro_image-5 allegro_audio-5 allegro_font-5 allegro_ttf-5 allegro_primitives-5` -o curse_of_theron *.c

Run the game:

    ./curse_of_theron

## How to play

Default or typical keyboard controls (please confirm exact bindings if different):

- Move: Arrow keys or A / D
- Jump: W or Space
- Shoot: Z or primary attack key
- Shoot upwards: Up + Shoot
- Menu: Navigate with arrow keys and confirm with Enter

The project contains a joystick mapping structure to support gamepad input. If you want the exact keys listed here, provide the preferred bindings or point to the control definitions in the code.

## Project structure (high level)

- main.c — Entry point and game state machine
- animation.c / animation.h — Sprite-sheet animation system
- character.c / character.h — Protagonist and enemy logic (HP, movement, collisions)
- bullet.c / bullet.h — Projectile handling using a linked list
- graphicsResources.c / graphicsResources.h — Drawing, HUD, camera, and music manager
- Personagens_Cenarios/ — Visual and audio assets (sprites, backgrounds, .ogg files)

## Architecture overview

- GameContext: Central structure holding display, timer, preferences (volume, difficulty), and other global state.
- GameState: Enum-based state machine controlling menu, settings, exploration, boss battles, etc.
- Fixed update rate (30 FPS) to keep physics and animation consistent across hardware.
- Animation: Dynamic arrays of ALLEGRO_BITMAP* for per-action frames.
- Bullets: Linked-list structure for managing multiple projectiles.

## Known issues

- Boss flame damage is currently applied every frame (30 times per second), which can result in very rapid HP loss while the player remains in the fire zone.
- Background wrap-around logic may show minor visual glitches when the player rapidly reverses direction at image boundaries.
- Music selection/volume may reset when returning from the settings menu to the main menu.

If you would like, I can open GitHub issues for these with suggested fixes.

## Contributing

Contributions are welcome. Suggested workflow:

1. Fork the repository.
2. Create a feature branch: git checkout -b feature/your-feature
3. Commit changes with clear messages.
4. Open a pull request describing the change and include screenshots or reproduction steps if applicable.

When reporting bugs or submitting features, please include:
- Platform and OS used for testing
- Build steps and any special dependencies
- Reproduction steps for bugs

## License

License: To be chosen. If you want the MIT license, I can add an appropriate LICENSE file and include the short license notice here.

## Credits

- Developed in C using Allegro 5
- Art and audio assets are located in Personagens_Cenarios/ — verify asset licenses before publishing

---

If you want any changes (controls, exact build flags, license selection, screenshots), tell me and I will update the README.
