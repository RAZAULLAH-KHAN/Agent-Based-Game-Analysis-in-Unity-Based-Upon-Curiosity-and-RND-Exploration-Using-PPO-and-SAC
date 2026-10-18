# Month 1 Execution & Git Push Plan: Hummingbirds Setup

**Project:** Agent-Based Game Analysis in Unity Based Upon Curiosity and RND Exploration Using PPO and SAC  
**Researcher:** Raza Ullah Khan  
**Timeline Alignment:** Figure 3 (Gantt Chart) — *Hummingbirds setup (M1 to M2.5)*

---

## 🎯 Month 1 Primary Objective
Establish a clean, reproducible Unity ML-Agents simulation environment for the Hummingbird task. By the end of Month 1, the environment, 3D assets, agent observation vector, continuous action space, reward functions, and initial baseline training configs will be fully implemented, tested, and tracked in Git.

---

## 📅 Week-by-Week & Daily Breakdown

### 🔹 Week 1: Project Foundation & Core Assets
*Focus: Environment initialization, packages, and 3D environment assets.*

- [x] **Day 1 (Completed & Pushed)**:
  - `Packages/manifest.json`: Unity ML-Agents `1.0.2-preview` and URP configuration.
  - `ProjectSettings/`: All 21 Unity editor and physics configurations (Unity 2019.3.15f1).
  - `requirements.txt`: Python ML-Agents `0.16.1` environment definition.
  - *Commit:* `feat(setup): initialize Unity 2019.3 project configuration, ML-Agents package manifest, and Python dependencies`

- [ ] **Day 2: 3D Environment Meshes & Materials**:
  - `Assets/Hummingbird/Meshes/`: Island terrain mesh, flower models, tree, and rocks.
  - `Assets/Hummingbird/Textures/` & `Materials/`: URP materials and textures for the island and flowers.
  - *Commit:* `feat(env): add 3D meshes, textures, and URP materials for island environment`

- [ ] **Day 3: Hummingbird 3D Model & Visual Setup**:
  - `Assets/Hummingbird/Meshes/Hummingbird.fbx`: Hummingbird geometry, beak collision mesh.
  - `Assets/Hummingbird/Materials/Bird/`: Feathers, beak, and eye materials.
  - *Commit:* `feat(agent): add Hummingbird 3D model, materials, and beak collider structure`

- [ ] **Day 4: Core Environment Prefabs**:
  - `Assets/Hummingbird/Prefabs/Flower.prefab`
  - `Assets/Hummingbird/Prefabs/FlowerArea.prefab`
  - `Assets/Hummingbird/Prefabs/Island.prefab`
  - *Commit:* `feat(env): assemble Flower, FlowerArea, and Island prefabs`

---

### 🔹 Week 2: Environment Logic & State Management
*Focus: C# scripts managing nectar replenishment, flower states, and game loop.*

- [ ] **Day 5: Flower Nectar Mechanics**:
  - `Assets/Hummingbird/Scripts/Flower.cs`:
    - Manages flower nectar level, active/empty visual state, and color transitions.
    - Feed nectar method with boundary checks.
  - *Commit:* `feat(env): implement Flower nectar replenishment and feed mechanics`

- [ ] **Day 6: Flower Area Coordinator**:
  - `Assets/Hummingbird/Scripts/FlowerArea.cs`:
    - Tracks all flowers on the island.
    - Resets flowers on episode start.
    - Calculates nearest flower relative vectors for agent sensors.
  - *Commit:* `feat(env): implement FlowerArea coordinator and relative distance queries`

- [ ] **Day 7: Game Manager & UI Controller**:
  - `Assets/Hummingbird/Scripts/GameManager.cs` & `UIController.cs`:
    - Match timer, score tracking, episode states (`MainMenu`, `Playing`, `Gameover`).
    - Nectar bar UI and win/loss logic.
  - *Commit:* `feat(ui): implement GameManager match controller and UIController score display`

- [ ] **Day 8: Unity Scenes Setup**:
  - `Assets/Hummingbird/Scenes/Training.unity`: 16 parallel training islands for accelerated RL.
  - `Assets/Hummingbird/Scenes/FlowerIsland.unity`: Single island playable scene for evaluation.
  - *Commit:* `feat(scenes): add 16-island parallel Training scene and single-island FlowerIsland scene`

---

### 🔹 Week 3: Agent Sensor, Actions & Reward Shaping
*Focus: C# HummingbirdAgent implementation (Observation space, Action space, and Reward design).*

- [ ] **Day 9: Observation Space (Sensors)**:
  - `Assets/Hummingbird/Scripts/HummingbirdAgent.cs` (`CollectObservations`):
    - Agent orientation (rotation quaternions / forward vector).
    - Relative vector from beak to nearest flower center.
    - Dot product alignment between beak forward vector and flower vector.
    - Agent velocity and boundary distances.
  - *Commit:* `feat(agent): implement continuous observation vector and flower orientation alignment`

- [ ] **Day 10: Action Space & Flight Physics**:
  - `HummingbirdAgent.cs` (`OnActionReceived`, `MoveAgent`):
    - 6-DOF continuous control (Pitch, Yaw, 3D translation forces).
    - Rigidbody velocity clamping and smooth steering dynamics.
  - *Commit:* `feat(agent): implement 6-DOF continuous flight physics and force controls`

- [ ] **Day 11: Reward Function Shaping**:
  - `HummingbirdAgent.cs` (Reward calculations):
    - Extrinsic reward for successful nectar drinking (`+0.01` per step).
    - Episode completion reward on full flower nectar drain.
    - Boundary collision penalty and out-of-bounds episode termination.
  - *Commit:* `feat(agent): configure extrinsic reward function and boundary penalty signals`

- [ ] **Day 12: Manual Heuristic Mode & Behavior Parameters**:
  - `HummingbirdAgent.cs` (`Heuristic` method):
    - WASD + Arrow key inputs for keyboard playability.
    - In-editor manual verification of flight physics and collision triggers.
  - *Commit:* `feat(agent): add keyboard heuristic control mode and behavior parameter presets`

---

### 🔹 Week 4: ML-Agents Baseline Configurations & Verification
*Focus: YAML configuration files for Condition 1 (PPO) and Condition 4 (SAC).*

- [ ] **Day 13: PPO Baseline Configuration**:
  - `config/ppo_baseline.yaml`:
    - Hyperparameters: batch size `2048`, buffer size `20480`, learning rate `3.0e-4`.
    - Extrinsic reward signal only (`strength: 1.0, gamma: 0.99`).
  - *Commit:* `config(mlagents): add Condition 1 PPO baseline configuration with extrinsic reward`

- [ ] **Day 14: SAC Baseline Configuration**:
  - `config/sac_baseline.yaml`:
    - Hyperparameters: off-policy buffer size `100000`, batch size `256`, tau `0.005`.
    - Extrinsic reward signal only.
  - *Commit:* `config(mlagents): add Condition 4 SAC baseline configuration with extrinsic reward`

- [ ] **Day 15: Baseline Multi-Seed Training Runner Script**:
  - `scripts/train_baseline.py` (or PowerShell wrapper):
    - Command runner to launch training runs with `--run-id` and `--seed`.
  - *Commit:* `feat(training): add automated training runner script with seed parameters`

- [ ] **Day 16: Pre-Trained Benchmark Model & Verification**:
  - `Assets/Hummingbird/NNModels/Hummingbird.nn`:
    - Verification run using pre-trained weights in `FlowerIsland.unity`.
  - *Commit:* `feat(models): include pre-trained benchmark model checkpoint for inference evaluation`

---

## 📌 Summary Checklist for Month 1
- [x] **Week 1:** Project settings, packages, Python dependencies (Day 1 pushed!)
- [ ] **Week 2:** Environment scripts, island prefabs, training scenes
- [ ] **Week 3:** Agent observations, actions, reward shaping, heuristic controls
- [ ] **Week 4:** PPO & SAC baseline configs, training runner, verification
