# 🔵 Roll & Collect

> A Unity 3D top-down collection game where you roll a ball, collect pickups, and avoid an enemy — all before time runs out!

---

## 📸 Screenshot

![Gameplay Screenshot](https://raw.githubusercontent.com/Adonis-Lee/Roll-A-Ball-Game/main/GamePlay_ScreenShots)
---

## 🎮 Gameplay

You control a **cyan ball** rolling around a walled arena. Your goal is to collect **12 yellow pickup cubes** scattered across the map before the **enemy** catches you.

- **Collect all 12 pickups** → You Win!
- **Enemy touches you** → You Lose!

---

## 🕹️ Controls

| Input | Action |
|-------|--------|
| `W / ↑` | Move Forward |
| `S / ↓` | Move Backward |
| `A / ←` | Move Left |
| `D / →` | Move Right |

> Uses Unity's new **Input System** (`PlayerInput` component).

---

## 📁 Project Structure

```
Assets/
├── Scripts/
│   ├── PlayerController.cs   # Player movement, pickup collection, win/lose logic
│   ├── CameraController.cs   # Smooth camera follow
│   ├── EnemyMovement.cs      # NavMesh-based enemy AI
│   └── Rotator.cs            # Pickup cube spin animation
```

---

## 🧩 Scripts Overview

### `PlayerController.cs`
Handles all core gameplay logic:
- **Physics movement** via `Rigidbody.AddForce()` using the Input System
- **Pickup collection** via trigger detection (Tag: `PickUp`)
- **Win condition**: Collect 12 pickups → shows "You Win!", destroys enemy
- **Lose condition**: Enemy collision → shows "You Lose!"
- Updates the **count UI** (TextMeshPro) on every pickup

### `CameraController.cs`
- Follows the player with a **fixed offset** calculated at start
- Runs in `LateUpdate()` to prevent camera jitter

### `EnemyMovement.cs`
- Uses **Unity NavMesh** to pathfind toward the player every frame
- Automatically navigates around obstacles in the arena

### `Rotator.cs`
- Rotates pickup cubes continuously on all 3 axes for visual flair
- `(15, 30, 45) * Time.deltaTime` for smooth, frame-rate-independent spin

---

## ⚙️ Setup & Requirements

- **Unity Version**: Unity 6 (or 2022 LTS+)
- **Packages Required**:
  - `com.unity.inputsystem` — New Input System
  - `com.unity.ai.navigation` — NavMesh Components
  - `com.unity.textmeshpro` — UI Text

### Scene Setup Checklist

- [ ] Player ball tagged as `Player`, has `Rigidbody` + `PlayerInput`
- [ ] Pickup cubes tagged as `PickUp`, have `Rotator.cs` + trigger colliders
- [ ] Enemy tagged as `Enemy`, has `NavMeshAgent` + `EnemyMovement.cs`
- [ ] NavMesh baked for the arena floor
- [ ] `CameraController` assigned the Player GameObject
- [ ] Canvas has `Count Text` (TMP) and `Win Text` objects wired to `PlayerController`

---

## 🏗️ How to Run

1. Clone or download the project
2. Open in **Unity Hub** → select correct Unity version
3. Open the main scene (`Assets/Scenes/Main.unity` or similar)
4. Press **Play** ▶️

---

## 🛠️ Built With

- [Unity](https://unity.com/) — Game Engine
- C# — Scripting Language
- Unity NavMesh — Enemy AI pathfinding
- Unity Input System — Player controls
- TextMeshPro — UI rendering

---

## 👤 Author

**Mehmet Anıl Ülkü**  
Electrical-Electronics & Computer Engineering Student   
GitHub: [Adonis-Lee](https://github.com/Adonis-Lee)

---

## 📄 License

This project was created for educational purposes as part of a Game Programming course.
