# The Curse of Theron - Castelvania_Game_Style

Jogo do gênero Run'n Gun

  Este projeto é um jogo de ação desenvolvido em C utilizando a biblioteca Allegro 5. O jogo mistura elementos de Run'n Gun com a estética de clássicos como Castlevania, apresentando mecânicas de combate à distância e combate corpo a corpo, sistema de animações por spritesheets e uma batalha

# Main Operation

    The main.c file serves as the core of the system. It is responsible for:

    Global Initialization: Configuring all basic Allegro components (Image, Audio, Fonts, Primitives, and Keyboard).

    Context Management: Utilizing the GameContext structure to centralize global information such as screen dimensions, music volume, and difficulty levels.

    State Machine: The game flow is controlled by a GameState enum. Using a while loop, the program determines whether to run the main menu, settings screen, exploration stage, boss battle, or the game-over screens (Victory or Game Over).

    Time Control: Maintaining a constant update rate (30 FPS) to ensure physics and animations occur smoothly across different hardware.

# Project Structure and Directories

    main.c: Program entry point and state machine controller.

    animation.c / animation.h: Animation system that loads spritesheets and manages frame switching based on accumulated time.

    character.c / character.h: Implementation of game entities (Protagonist and Enemies), containing HP logic, movement physics, and collision detection.

    Bullet.c / Bullet.h: Projectile mechanics using linked lists to allow multiple shots on screen simultaneously.

    graphicsResources.c / graphicsResources.h: Scene and resource manager, responsible for drawing the interface (HUD), managing the camera, and music.

    /Personagens_Cenários: Directory containing all visual assets (sprites, backgrounds) and audio files (.ogg tracks).

# General Data Structures Used

    struct GameContext: The master structure that stores the hardware state (display, timer) and user preferences (volume, difficulty).

    struct Protagonist & struct Character: Structures defining the game's living entities. They store pointers to various animations (idle, running, attack) and a struct Joystick that maps movement intentions.

    struct Animation: Manages a dynamic array of ALLEGRO_BITMAP* representing the individual frames of an action.

    struct bullet (Linked List): Used to dynamically manage projectiles. Each bullet tracks its origin (hero or enemy) and its trajectory (left, right, or up).

# Extra Features Implemented

    Beyond the basic mechanics, the game includes:

    Adjustable Difficulty: A settings menu with three levels (Easy, Medium, and Hard) that modify enemy HP and damage.

    Life Configuration: Players can choose between "Normal," "Double Life," or "HitKill" (one-hit death) modes.

    Language System: An integrated bilingual interface, allowing real-time switching between Portuguese and English in the menu.

    Vertical Shooting Mechanic: The hero can shoot upwards, utilizing rotated sprites.

    Objective-Based Progression: Access to the Boss is granted only after defeating a specific number of enemies in the stage.

    Multi-Stage Boss Battle: The "Demon King" features its own state machine, alternating between projectile attacks and a special fire-based area attack.

# Known Errors and Issues

    Damage per Frame: Boss flame damage is applied every frame (30 times per second), which can lead to extremely rapid health loss if the player does not exit the danger zone immediately.

    Camera Limitations: The background wrap-around logic works well in linear movement but may show minor visual glitches if the player switches directions repeatedly and rapidly at the image boundary.

    Music Bug: The music menu keeps reseting every time you go to settings and then go back to the menu.
