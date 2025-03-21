# **Eyelian Rush - Game Documentation**

## **1. Introduction**

#### **1.1. Overview**

**Eyelian Rush** is a **2D multiplayer shooter** where players control characters, eliminate enemies, and collect coins. The game features:

- **Single-player and two-player modes**
- **Enemy AI** that tracks and attacks players
- **Projectile system** for shooting
- **Dynamic camera movement** for large maps
- **Pause and menu systems**

The game is built using **Pygame**, a popular Python library for game development.

#### **1.2. Objectives**

- Survive enemy attacks
- Collect as many coins as possible
- Defeat enemies using bullets

---

## **2. Setup & Requirements**

### **2.1. System Requirements**

- OS: Windows, macOS, or Linux
- Python 3.8+
- Pygame installed

### **2.2. Installing Dependencies**

Install **Pygame** and other dependencies with:

```sh
pip install pygame pyinstall
```

### **2.3. Running the Game**

Execute the main script using:

```sh
python Main_game.py
```

### **2.4. Packaging the Game**

Convert the game into an executable for distribution:

```sh
pyinstaller --onefile --add-data "Picture;Picture" --add-data "Fonts;Fonts" Eyelian_Rush.py
```

---

## **3. Game Controls**

| **Action** | **Player 1** | **Player 2**  |
| ---------- | ------------ | ------------- |
| Move Up    | `W`          | `Arrow Up`    |
| Move Down  | `S`          | `Arrow Down`  |
| Move Left  | `A`          | `Arrow Left`  |
| Move Right | `D`          | `Arrow Right` |
| Pause Game | `ESC`        | `ESC`         |

---

## **4. Game Mechanics**

### **4.1. Player Movement**

- Players can **move up, down, left, and right** on the map.

### **4.2. Shooting System**

- Each player has a **shoot cooldown** to prevent spamming bullets.
- Bullets **follow a trajectory** towards the enemy.
- Players must **aim carefully** to defeat enemies.

### **4.3. Enemy AI**

- Enemies **detect and chase** the nearest player.
- They attack players when **within a certain range**.
- The game **spawns enemies dynamically** based on player progress.

### **4.4. Coins & Scoring**

- Coins appear on the map at random locations.
- Players must **move over the coins** to collect them.
- Collected coins contribute to the **final score**.

### **4.5. Camera System**

- The game world is **larger than the screen size**.
- A **camera system follows** the players dynamically.

### **4.6. Game Over Conditions**

- A player loses when **their health reaches zero**.
- The game **ends if both players are defeated**.

---

## **5. Code Structure**

### **5.1. Main Game Loop**

Handles the **game flow**:

1. **Menu selection**
2. **Initialize characters, enemies, projectiles**
3. **Run the game loop**
4. **Pause and exit conditions**

---

## **6. Class Explanations**

### **6.1. `Button` Class** – Manages **UI buttons** in the menu and pause screen.

- **Attributes:**
  - **`image`** – Default appearance
  - **`hover_image`** – Appearance when hovered
  - **`rect`** – Defines position and size
  - **`clicked`** – Prevents multiple rapid clicks
- **Methods:**
  - **`draw(surface)`** – Draws the button and detects clicks

### **6.2. `Camera` Class** – Handles **map scrolling** by following players.

- **Methods:**
  - **`apply(entity)`** – Moves entities based on camera position
  - **`update(targets)`** – Centers the camera on players

### **6.3. `Tank` Class** – Represents a **player-controlled character**.

- **Attributes:**
  - **`speed`** – Movement speed
  - **`flipped`** – Tracks player orientation
  - **`shoot_cooldown`** – Time delay between shots
- **Methods:**
  - **`update()`** – Moves and animates the player
  - **`shoot(enemies)`** – Fires a bullet at the nearest enemy

### **6.4. `Projectile` Class** – Handles **bullets** fired by players.

- **Methods:**
  - **`update()`** – Moves towards the target and rotates

### **6.5. `Enemy` Class** – Represents **enemies** that chase and attack players.

- **Methods:**
  - **`update(player_tanks)`** – Moves toward the closest player

### **6.6. `Coin` Class** – Represents a **collectible gold coin**.

- **Methods:**
  - **`update()`** – Animates the coin

---

## **7. Menu & Pause System**

### **7.1. `menu(screen) -> str`**

Displays the **main menu**.  
Returns:

- `"1p"` → Start Single-player
- `"2p"` → Start Two-player
- `"quit"` → Exit

### **7.2. `pause(screen) -> str`**

Pauses the game.  
Returns:

- `"resume"` → Continue
- `"quit"` → Exit

---

## **8. Collision System**

### **8.1. Bullet vs. Enemy**

- When a bullet hits an enemy, the enemy is **destroyed**.
- The player **earns points** for each enemy defeated.

### **8.2. Player vs. Enemy**

- Enemies deal **damage** when touching a player.
- Players can **lose health** and eventually **die**.

### **8.3. Player vs. Coin**

- When a player touches a coin, it is **collected**.
- The player’s **score increases**.

---

## **9. Multiplayer System**

The game supports **local two-player mode**, where:

- **P1 uses WASD & Spacebar**
- **P2 uses Arrow Keys & Enter**

Both players **share the same screen**.

---

## **10. Future Improvements**

### **10.1. Planned Features**

- **More enemy types** (faster enemies, armored enemies)
- **Power-ups** (shield, speed boost, rapid fire)
- **Online Multiplayer** (using sockets or Pygame networking)
- **Weapon Upgrades** (different types of bullets)
- **Larger Maps** (with obstacles and structures)

### **10.2. Performance Optimizations**

- Improve **enemy AI** for better movement.
- Optimize **collision detection** for smoother gameplay.

---

## **11. Conclusion**

This documentation provides a **detailed reference** for the **Tank Battle** game, explaining its **setup, gameplay mechanics, classes, and future development plans**. The game is a **fun, arcade-style shooter** that can be expanded with more features in the future.🚀
