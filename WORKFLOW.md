# 🎮 Cursed Dungeon

> A 2D top-down roguelike game and lightweight game-engine project built from scratch in **C**.

The goal of this project is not only to make a game, but to understand how a game works internally: game loops, input handling, rendering, collision detection, entity management, procedural generation, AI, combat, memory management, file I/O, and cross-platform builds.

---

# 1. Project Goals

## Primary Goal

Build a playable 2D roguelike game in C with:

* Player movement
* Dungeon exploration
* Procedurally generated maps
* Multiple enemy types
* Enemy AI
* Combat
* Weapons
* Inventory
* Items
* XP and leveling
* Boss fights
* Save/load
* Audio
* UI
* Animations
* Cross-platform builds

## Technical Goal

Use the project to learn and demonstrate:

* C programming
* Pointers
* Structures
* Dynamic memory
* Arrays
* Linked lists
* File I/O
* Algorithms
* Data structures
* Random number generation
* Game loops
* Collision detection
* Basic physics
* AI
* Software architecture
* Build systems
* Testing
* Debugging
* Git/GitHub
* Cross-platform development

---

# 2. Target Platforms

Development will primarily happen on:

* Linux

The final project should target:

* Linux
* Windows
* macOS

The code should avoid unnecessary OS-specific dependencies.

---

# 3. Technology Stack

| Component            | Technology           |
| -------------------- | -------------------- |
| Programming Language | C17                  |
| Compiler             | GCC / Clang          |
| Graphics             | raylib               |
| Build System         | CMake                |
| Version Control      | Git                  |
| Repository           | GitHub               |
| Audio                | raylib               |
| Images               | PNG                  |
| Audio Files          | WAV / OGG            |
| Testing              | CTest + custom tests |
| Documentation        | Markdown             |

---

# 4. Development Philosophy

The project will be developed in layers.

```text
C Fundamentals
      ↓
Terminal Prototype
      ↓
Game Logic
      ↓
Game Architecture
      ↓
Procedural Dungeon
      ↓
Enemy AI
      ↓
Combat
      ↓
Inventory
      ↓
Save System
      ↓
Graphics
      ↓
Audio
      ↓
UI
      ↓
Polishing
      ↓
Testing
      ↓
Cross-Platform Build
      ↓
Release
```

Do not start by making the game visually impressive.

Make it **functionally correct first**.

---

# 5. Phase 0 — Project Planning

## Objective

Define what the game is before writing code.

## Tasks

* [ ] Decide game name
* [ ] Write game concept
* [ ] Define player mechanics
* [ ] Define enemy types
* [ ] Define combat mechanics
* [ ] Define dungeon mechanics
* [ ] Define item system
* [ ] Define progression system
* [ ] Define win condition
* [ ] Define lose condition
* [ ] Define minimum viable version

## Deliverable

Create:

```text
GAME_DESIGN.md
```

---

# 6. Game Concept

## Genre

2D top-down roguelike.

## Core Gameplay Loop

```text
Explore
   ↓
Find enemies
   ↓
Fight
   ↓
Collect items
   ↓
Gain XP
   ↓
Become stronger
   ↓
Explore deeper
   ↓
Fight boss
   ↓
Complete dungeon
```

---

# 7. Player

The player should have:

```text
Position
Health
Maximum Health
Attack
Defense
Level
Experience
Weapon
Inventory
```

## Player actions

* Move
* Attack
* Pick up items
* Use items
* Change weapon
* Open inventory
* Interact with objects
* Save game
* Pause game

---

# 8. Enemy System

Start with a small number of enemy types.

## Enemy 1 — Goblin

Characteristics:

* Fast
* Low health
* Melee attack

## Enemy 2 — Skeleton

Characteristics:

* Medium speed
* Medium health
* Ranged attack

## Enemy 3 — Boss

Characteristics:

* High health
* High damage
* Multiple attack patterns
* Special abilities

Additional enemies can be added later.

---

# 9. Dungeon

The dungeon should contain:

* Rooms
* Corridors
* Walls
* Floors
* Doors
* Items
* Enemies
* Treasure
* Boss room

Example:

```text
┌─────────────┐
│             │
│    ROOM     │
│             │
└──────┬──────┘
       │
       │
┌──────┴──────┐
│             │
│    ROOM     │
│             │
└─────────────┘
```

---

# 10. Phase 1 — C Fundamentals

Before starting the actual game, make sure the required C concepts are understood.

## Topics

* [ ] Variables
* [ ] Data types
* [ ] Operators
* [ ] Conditions
* [ ] Loops
* [ ] Functions
* [ ] Arrays
* [ ] Strings
* [ ] Structures
* [ ] Enumerations
* [ ] Pointers
* [ ] Pointer arithmetic
* [ ] Memory allocation
* [ ] `malloc`
* [ ] `calloc`
* [ ] `realloc`
* [ ] `free`
* [ ] File handling
* [ ] Header files
* [ ] Multiple source files
* [ ] Compilation
* [ ] Linker basics

## Goal

Be able to understand and debug your own C code without relying on generated code.

---

# 11. Phase 2 — Project Skeleton

Create the initial repository structure.

```text
CursedDungeon/
│
├── src/
├── include/
├── assets/
├── tests/
├── docs/
├── saves/
│
├── CMakeLists.txt
├── README.md
├── GAME_DESIGN.md
├── PROJECT_WORKFLOW.md
├── CHANGELOG.md
└── LICENSE
```

At this stage, the project does not need to contain the complete game.

---

# 12. Phase 3 — Terminal Prototype

Before using graphics, create a terminal version.

Example:

```text
########################
#                      #
#       @              #
#              E       #
#                      #
#          E           #
#                      #
########################

HP: 100
LEVEL: 1
XP: 0
```

Where:

```text
@ = Player
E = Enemy
# = Wall
. = Floor
```

## Implement

* [ ] Player movement
* [ ] Walls
* [ ] Collision
* [ ] Enemy placement
* [ ] Basic attacks
* [ ] Health
* [ ] Enemy death
* [ ] Player death
* [ ] Game restart

## Goal

Have a complete playable text-based prototype.

---

# 13. Phase 4 — Game Loop

Build the core game loop.

Conceptually:

```text
Initialize
    ↓
Get Input
    ↓
Update Game
    ↓
Collision Detection
    ↓
Enemy AI
    ↓
Combat
    ↓
Render
    ↓
Repeat
```

The loop should continue until:

```text
Player exits
        OR
Player dies
        OR
Game completed
```

---

# 14. Phase 5 — Game State

Define major game states.

```text
MAIN_MENU
    ↓
PLAYING
    ↓
PAUSED
    ↓
GAME_OVER
    ↓
VICTORY
```

Possible flow:

```text
             MAIN MENU
                 │
       ┌─────────┴─────────┐
       ↓                   ↓
   NEW GAME             LOAD GAME
       │                   │
       └─────────┬─────────┘
                 ↓
               PLAY
                 │
        ┌────────┴────────┐
        ↓                 ↓
     DEATH              BOSS
        ↓                 ↓
   GAME OVER           VICTORY
```

---

# 15. Phase 6 — Entity System

Create a common concept for game entities.

Entities may include:

```text
Player
Enemy
Item
Projectile
NPC
Door
Chest
Boss
```

Each entity may have:

```text
Position
Size
Health
Type
State
```

The system should allow multiple entities to exist simultaneously.

---

# 16. Phase 7 — Collision System

Implement collision detection.

## Required collisions

### Player vs Wall

```text
Player → Wall

Prevent movement
```

### Player vs Enemy

```text
Player → Enemy

Prevent overlap
```

### Projectile vs Enemy

```text
Projectile → Enemy

Apply damage
```

### Player vs Item

```text
Player → Item

Pick up item
```

---

# 17. Phase 8 — Procedural Dungeon Generation

Make dungeon layouts generated automatically.

The same game should not always produce the same dungeon.

Example:

```text
Seed
 ↓
Generate Rooms
 ↓
Connect Rooms
 ↓
Generate Corridors
 ↓
Place Enemies
 ↓
Place Items
 ↓
Place Boss
 ↓
Playable Dungeon
```

## Requirements

* [ ] Random seed
* [ ] Room generation
* [ ] Corridor generation
* [ ] Wall generation
* [ ] Room connectivity
* [ ] Enemy placement
* [ ] Item placement
* [ ] Boss room
* [ ] Difficulty progression

---

# 18. Phase 9 — Enemy AI

Start simple.

## Basic AI

```text
Is player nearby?
       │
   ┌───┴───┐
   ↓       ↓
  YES      NO
   ↓       ↓
Attack   Patrol
```

## Advanced AI

Eventually support:

```text
IDLE
 ↓
PATROL
 ↓
DETECT PLAYER
 ↓
CHASE
 ↓
ATTACK
 ↓
RETREAT / DEAD
```

Different enemies should behave differently.

---

# 19. Phase 10 — Combat System

Implement:

```text
Player Attack
      ↓
Target Detection
      ↓
Damage Calculation
      ↓
Defense
      ↓
Critical Hit
      ↓
Apply Damage
      ↓
Enemy Dead?
```

## Features

* [ ] Melee attacks
* [ ] Ranged attacks
* [ ] Damage
* [ ] Defense
* [ ] Critical hits
* [ ] Attack cooldown
* [ ] Enemy death
* [ ] XP reward
* [ ] Boss attacks

---

# 20. Phase 11 — Weapons

Start with:

```text
Wooden Sword
Iron Sword
Fire Sword
```

Later:

```text
Bow
Magic Staff
Axe
Rare Weapons
Legendary Weapons
```

Each weapon can have:

```text
Damage
Attack Speed
Range
Critical Chance
Special Ability
```

---

# 21. Phase 12 — Items

Create an item system.

Possible categories:

```text
WEAPON
ARMOR
POTION
SCROLL
KEY
QUEST_ITEM
```

Examples:

```text
Health Potion
Mana Potion
Fire Scroll
Dungeon Key
Iron Sword
Magic Ring
```

---

# 22. Phase 13 — Inventory

Example UI:

```text
┌─────────────────────────┐
│       INVENTORY         │
├─────────────────────────┤
│ 1  Iron Sword           │
│ 2  Health Potion        │
│ 3  Fire Scroll          │
│ 4  Empty                │
│ 5  Empty                │
└─────────────────────────┘
```

## Requirements

* [ ] Add item
* [ ] Remove item
* [ ] Use item
* [ ] Equip item
* [ ] Drop item
* [ ] Inventory capacity
* [ ] Item selection

---

# 23. Phase 14 — Player Progression

Add:

```text
XP
 ↓
Level Up
 ↓
Increase Stats
```

Example:

```text
LEVEL 1
HP: 100
ATK: 10

       ↓

LEVEL 2
HP: 120
ATK: 13
```

Possible attributes:

* Health
* Attack
* Defense
* Speed
* Critical Chance

---

# 24. Phase 15 — Save / Load

Implement persistent game state.

## Save

Store:

```text
Player
 ├── Position
 ├── Health
 ├── Level
 ├── XP
 ├── Weapon
 └── Inventory

Dungeon
 ├── Seed
 ├── Floor
 └── Progress
```

## Menu

```text
NEW GAME
LOAD GAME
SAVE GAME
QUIT
```

---

# 25. Phase 16 — Introduce raylib

Once the game logic works, introduce graphical rendering.

The architecture should look like:

```text
              GAME LOGIC
                  │
        ┌─────────┴─────────┐
        ↓                   ↓
     INPUT               RENDER
        │                   │
        ↓                   ↓
     GAME STATE          raylib
                            │
                            ↓
                         WINDOW
```

The game logic should not depend unnecessarily on rendering code.

---

# 26. Phase 17 — Graphics

Replace terminal characters with graphics.

Add:

* [ ] Player sprite
* [ ] Enemy sprites
* [ ] Dungeon tiles
* [ ] Weapons
* [ ] Items
* [ ] UI
* [ ] Menus
* [ ] Animations

Target:

```text
┌───────────────────────────────────┐
│                                   │
│       🧱 🧱 🧱                    │
│       🧱 🧙 🧱        👹          │
│       🧱   🧱                     │
│                                   │
│              🗡️                   │
│                                   │
├───────────────────────────────────┤
│ HP ████████░░    LEVEL 3          │
│ XP █████░░░░░    FLOOR 2          │
└───────────────────────────────────┘
```

---

# 27. Phase 18 — UI

Create:

## Main Menu

```text
CURSED DUNGEON

NEW GAME
LOAD GAME
SETTINGS
QUIT
```

## Pause Menu

```text
PAUSED

RESUME
SAVE GAME
SETTINGS
QUIT
```

## HUD

Display:

* Health
* XP
* Level
* Current weapon
* Floor
* Selected item

---

# 28. Phase 19 — Audio

Add:

* [ ] Background music
* [ ] Attack sound
* [ ] Enemy hit sound
* [ ] Enemy death sound
* [ ] Player damage sound
* [ ] Item pickup sound
* [ ] Door sound
* [ ] Boss music
* [ ] Victory sound
* [ ] Game-over sound

Only use assets with licenses that allow your intended use.

Keep a record of asset sources and licenses.

---

# 29. Phase 20 — Animation

Add:

* [ ] Player idle animation
* [ ] Player movement animation
* [ ] Attack animation
* [ ] Enemy movement
* [ ] Enemy death
* [ ] Item effects
* [ ] Boss animation

---

# 30. Phase 21 — Visual Effects

Add polish gradually.

Possible effects:

* Hit particles
* Attack effects
* Damage numbers
* Screen shake
* Flash effects
* Death particles
* Door animation
* Lighting
* Shadows

Do not add effects until the underlying gameplay works correctly.

---

# 31. Phase 22 — Difficulty System

Create increasing difficulty.

```text
FLOOR 1
   ↓
Easy enemies
   ↓
FLOOR 2
   ↓
More enemies
   ↓
FLOOR 3
   ↓
Stronger enemies
   ↓
FLOOR 4
   ↓
Elite enemies
   ↓
BOSS
```

Possible difficulty variables:

* Enemy health
* Enemy damage
* Enemy count
* Enemy speed
* Dungeon complexity
* Item rarity

---

# 32. Phase 23 — Boss System

Create a dedicated boss.

The boss should have multiple phases.

Example:

```text
BOSS PHASE 1
Normal attack
      ↓
Health < 70%
      ↓
BOSS PHASE 2
Faster attacks
      ↓
Health < 40%
      ↓
BOSS PHASE 3
Special attacks
      ↓
Boss defeated
      ↓
VICTORY
```

---

# 33. Phase 24 — Testing

Testing should happen throughout development.

## Test

### Player

* [ ] Movement
* [ ] Collision
* [ ] Health
* [ ] Death
* [ ] Level up

### Enemies

* [ ] Spawn
* [ ] Movement
* [ ] AI
* [ ] Attack
* [ ] Death

### Dungeon

* [ ] Generation
* [ ] Connectivity
* [ ] Collision
* [ ] Boss placement

### Inventory

* [ ] Add
* [ ] Remove
* [ ] Use
* [ ] Equip
* [ ] Drop

### Save System

* [ ] Save
* [ ] Load
* [ ] Corrupt save handling
* [ ] Missing save handling

---

# 34. Phase 25 — Debugging

Learn to use:

* GDB
* AddressSanitizer
* UndefinedBehaviorSanitizer
* Valgrind
* compiler warnings

Compile with strong warnings.

The goal is:

```text
No warnings
No memory leaks
No undefined behavior
No crashes
```

---

# 35. Phase 26 — Performance

Measure before optimizing.

Potential areas:

```text
Rendering
Enemy AI
Collision Detection
Dungeon Generation
Memory Allocation
```

Later investigate:

* Frame rate
* CPU usage
* Memory usage
* Number of entities
* Update time
* Render time

Do not optimize code simply because it "looks slow."

Measure first.

---

# 36. Phase 27 — Refactoring

Once the game works:

Review the codebase.

Look for:

* Duplicate code
* Huge functions
* Huge files
* Poor naming
* Global variables
* Unnecessary allocations
* Memory leaks
* Tight coupling
* Platform-specific code

Refactor before final release.

---

# 37. Phase 28 — Cross-Platform Support

Use CMake to manage builds.

Target:

```text
Linux
Windows
macOS
```

Test:

```text
Build
Run
Save
Load
Audio
Input
Rendering
```

on each platform.

Avoid relying on Linux-specific APIs unless absolutely necessary.

---

# 38. Phase 29 — Release Builds

Create release configurations.

## Debug

Used during development.

Contains:

* Debug symbols
* Sanitizers
* Extra checks
* Logging

## Release

Used for players.

Contains:

* Optimizations
* No unnecessary debug output
* Packaged assets
* Clean executable

---

# 39. Phase 30 — Git Workflow

Use Git throughout development.

Suggested branches:

```text
main
develop
feature/player
feature/dungeon
feature/combat
feature/ui
```

Commit frequently.

Good commits:

```text
feat: add player movement
feat: add collision detection
feat: add enemy system
feat: add dungeon generation
fix: prevent player wall clipping
fix: resolve enemy collision bug
refactor: separate combat system
docs: update build instructions
```

Avoid:

```text
update
changes
final
final2
working
new
```

---

# 40. Phase 31 — Documentation

Create:

```text
README.md
GAME_DESIGN.md
PROJECT_WORKFLOW.md
CHANGELOG.md
LICENSE
```

README should include:

## Project

What is Cursed Dungeon?

## Features

List major features.

## Screenshots

Add gameplay screenshots.

## Gameplay Video

Add a short demo.

## Controls

Example:

```text
WASD       Move
Mouse      Aim
Left Click Attack
E          Interact
I          Inventory
ESC        Pause
```

## Build

Explain how to build on each OS.

## Architecture

Explain the major systems.

## Technical Details

Explain:

* Game loop
* Rendering
* Collision
* AI
* Dungeon generation
* Save system

## Roadmap

Show completed and future features.

---

# 41. Phase 32 — Portfolio Presentation

The final project should demonstrate more than gameplay.

Show:

```text
C
│
├── Memory Management
├── Data Structures
├── Algorithms
├── File I/O
├── Game Architecture
├── AI
├── Procedural Generation
├── Graphics
├── Audio
├── Debugging
├── Testing
├── CMake
└── Cross-platform Development
```

---

# 42. Final Repository

Target structure:

```text
CursedDungeon/
│
├── src/
│   ├── main.c
│   ├── game.c
│   ├── player.c
│   ├── enemy.c
│   ├── combat.c
│   ├── collision.c
│   ├── dungeon.c
│   ├── entity.c
│   ├── item.c
│   ├── inventory.c
│   ├── save.c
│   ├── audio.c
│   └── renderer.c
│
├── include/
│   ├── game.h
│   ├── player.h
│   ├── enemy.h
│   ├── combat.h
│   ├── collision.h
│   ├── dungeon.h
│   ├── entity.h
│   ├── item.h
│   ├── inventory.h
│   ├── save.h
│   ├── audio.h
│   └── renderer.h
│
├── assets/
│   ├── sprites/
│   ├── textures/
│   ├── sounds/
│   ├── music/
│   └── fonts/
│
├── tests/
│
├── docs/
│   ├── architecture.md
│   ├── dungeon-generation.md
│   ├── enemy-ai.md
│   └── save-system.md
│
├── saves/
│
├── CMakeLists.txt
├── README.md
├── GAME_DESIGN.md
├── PROJECT_WORKFLOW.md
├── CHANGELOG.md
└── LICENSE
```

---

# 43. Minimum Viable Game

Before adding advanced features, the game must reach this state:

```text
┌─────────────────────────────┐
│                             │
│        DUNGEON              │
│                             │
│      PLAYER                 │
│        ↓                    │
│      ENEMY                  │
│        ↓                    │
│      COMBAT                 │
│        ↓                    │
│      ITEM                   │
│        ↓                    │
│      EXIT                   │
│        ↓                    │
│      BOSS                   │
│        ↓                    │
│     VICTORY                 │
│                             │
└─────────────────────────────┘
```

Minimum features:

* [ ] Player movement
* [ ] Dungeon
* [ ] Collision
* [ ] At least one enemy
* [ ] Combat
* [ ] Health
* [ ] Death
* [ ] Basic item
* [ ] Boss
* [ ] Victory condition

Only after this should advanced features become the priority.

---

# 44. Version Roadmap

## v0.1 — Prototype

* [ ] Terminal map
* [ ] Player movement
* [ ] Basic collision

## v0.2 — Gameplay

* [ ] Enemies
* [ ] Combat
* [ ] Health
* [ ] Death

## v0.3 — Dungeon

* [ ] Rooms
* [ ] Corridors
* [ ] Procedural generation

## v0.4 — Progression

* [ ] XP
* [ ] Levels
* [ ] Weapons
* [ ] Items
* [ ] Inventory

## v0.5 — Persistence

* [ ] Save
* [ ] Load
* [ ] Game states

## v0.6 — Graphics

* [ ] raylib
* [ ] Sprites
* [ ] Rendering
* [ ] UI

## v0.7 — AI

* [ ] Enemy states
* [ ] Different enemy behaviors
* [ ] Boss AI

## v0.8 — Audio & Polish

* [ ] Music
* [ ] Sound effects
* [ ] Animations
* [ ] Particles

## v0.9 — Testing

* [ ] Unit tests
* [ ] Memory testing
* [ ] Sanitizers
* [ ] Performance testing

## v1.0 — Release

* [ ] Linux build
* [ ] Windows build
* [ ] macOS build
* [ ] Documentation
* [ ] Screenshots
* [ ] Gameplay video
* [ ] GitHub release

---

# 45. Definition of Done

The project is considered complete when:

* [ ] Game is playable from beginning to end
* [ ] Dungeon generation works
* [ ] Combat works
* [ ] Enemy AI works
* [ ] Boss fight works
* [ ] Inventory works
* [ ] Save/load works
* [ ] UI works
* [ ] Audio works
* [ ] No known critical crashes
* [ ] No known memory leaks
* [ ] Build works on Linux
* [ ] Windows build tested
* [ ] macOS build tested
* [ ] README completed
* [ ] Documentation completed
* [ ] License included
* [ ] Screenshots added
* [ ] Gameplay video recorded
* [ ] GitHub repository cleaned
* [ ] v1.0 release created

---

# 46. Final Project Architecture

The final system should conceptually look like this:

```text
                         CURSED DUNGEON
                               │
                 ┌─────────────┴─────────────┐
                 │                           │
             GAME ENGINE                   GAME
                 │                           │
      ┌──────────┼──────────┐        ┌───────┴────────┐
      │          │          │        │                │
    Input     Update     Render    Player          Enemies
      │          │          │        │                │
      │      ┌───┴────┐     │     Combat             AI
      │      │        │     │        │                │
      │   Physics   Logic   │     Inventory          AI State
      │      │        │     │        │
      │   Collision  State  │      Items
      │                   raylib
      │                      │
      └──────────────────────┘

                 Supporting Systems
                         │
       ┌─────────┬───────┼────────┬──────────┐
       ↓         ↓       ↓        ↓          ↓
     Audio     Save    Config    Random    Logging
```

---

# 47. The Most Important Rule

Do not try to finish everything immediately.

Build in this order:

```text
1. Make it work
        ↓
2. Make it organized
        ↓
3. Make it graphical
        ↓
4. Make it polished
        ↓
5. Make it portable
        ↓
6. Make it release-ready
```

The finished result should not just be:

> "I made a game in C."

It should be:

> **"I designed and implemented a cross-platform 2D roguelike and lightweight game engine in C, including the game loop, entity system, collision detection, procedural dungeon generation, enemy AI, combat, persistence, rendering, audio, testing, and build infrastructure."**

That is the actual portfolio value of the project.
