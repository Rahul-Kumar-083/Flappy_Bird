# 🐦 Flappy Bird AI using Deep Q-Learning (DQN)

A Deep Reinforcement Learning project where an AI agent learns to play Flappy Bird using the Deep Q-Network (DQN) algorithm implemented in PyTorch.

## 📌 Overview

This project trains an autonomous Flappy Bird agent using:

* Deep Q-Networks (DQN)
* Experience Replay
* Target Network Synchronization
* Epsilon-Greedy Exploration Strategy

The agent interacts with the Flappy Bird environment, learns from rewards, and gradually improves its performance through reinforcement learning.

---

## 🚀 Features

* Deep Q-Learning implementation using PyTorch
* Experience Replay Buffer
* Target Network for stable learning
* Configurable hyperparameters through YAML
* Model checkpoint saving
* Training and evaluation modes
* GPU/CUDA/MPS support

---

## 📂 Project Structure

```text
.
├── agent.py                  # Main training/testing script
├── dqn.py                    # Deep Q-Network architecture
├── experience_replay.py      # Replay memory implementation
├── game_flappy_bird.py       # Manual Flappy Bird gameplay
├── parameters.yaml           # Hyperparameter configuration
├── runs/
│   ├── *.pt                  # Saved model weights
│   └── *.log                 # Training logs
└── README.md
```

---

## 🧠 Deep Q-Network Architecture

```text
Input Layer (State Space)
        ↓
Linear Layer (256 Neurons)
        ↓
ReLU Activation
        ↓
Output Layer (Actions)
```

Actions:

| Action | Description |
| ------ | ----------- |
| 0      | Do Nothing  |
| 1      | Flap        |

---

## ⚙️ Installation

### Clone Repository

```bash
git clone https://github.com/Rahul-Kumar-083/Flappy_Bird.git
cd Flappy_Bird
```

### Install Dependencies

```bash
pip install torch gymnasium flappy-bird-gymnasium pygame pyyaml
```

---

## 🏋️ Training the Agent

Run training using a parameter set defined in `parameters.yaml`.

```bash
python agent.py flappybirdv0 --train
```

During training:

* Experiences are stored in replay memory.
* Mini-batches are sampled randomly.
* The policy network is updated using gradient descent.
* The target network is synchronized periodically.
* The best-performing model is automatically saved.

Saved files:

```text
runs/
├── flappybirdv0.pt
└── flappybirdv0.log
```

---

## 🎮 Testing the Trained Agent

Run the trained model:

```bash
python agent.py flappybirdv0
```

The agent will load the saved model and play Flappy Bird automatically.

---

## 📊 Hyperparameters

Example configuration:

```yaml
default:
  alpha: 0.001
  gamma: 0.99

  epsilon_init: 1.0
  epsilon_min: 0.01
  epsilon_decay: 0.995

  replay_memory_size: 100000
  mini_batch_size: 64

  network_sync_rate: 1000
  reward_threshold: 10000
```

### Parameter Description

| Parameter          | Description                         |
| ------------------ | ----------------------------------- |
| alpha              | Learning rate                       |
| gamma              | Discount factor                     |
| epsilon_init       | Initial exploration rate            |
| epsilon_min        | Minimum exploration rate            |
| epsilon_decay      | Exploration decay factor            |
| replay_memory_size | Replay buffer size                  |
| mini_batch_size    | Batch size for training             |
| network_sync_rate  | Frequency of target network updates |
| reward_threshold   | Maximum reward per episode          |

---

## 🔄 DQN Training Workflow

```text
Observe State
      ↓
Select Action
      ↓
Execute Action
      ↓
Receive Reward
      ↓
Store Experience
      ↓
Sample Mini-Batch
      ↓
Update Policy Network
      ↓
Sync Target Network
      ↓
Repeat
```

---

## 📈 Reinforcement Learning Components

### Experience Replay

Stores previous experiences:

```text
(State, Action, Next State, Reward, Done)
```

Benefits:

* Breaks temporal correlations
* Improves training stability
* Increases sample efficiency

### Target Network

A separate network used to calculate target Q-values.

Benefits:

* Prevents oscillating Q-values
* Stabilizes learning

### Epsilon-Greedy Strategy

Balances:

* Exploration (random actions)
* Exploitation (best-known actions)

Exploration gradually decreases over time.

---

## 🖥 Device Support

The project automatically selects:

1. Apple Silicon (MPS)
2. NVIDIA CUDA GPU
3. CPU

No manual configuration is required.

---

## 📚 Technologies Used

* Python
* PyTorch
* Gymnasium
* Flappy Bird Gymnasium
* PyGame
* YAML

---

## 📜 License

This project is open-source and available under the MIT License.

---

## 👨‍💻 Author

Built as a Deep Reinforcement Learning project to explore how Deep Q-Networks can learn complex game-playing behavior from raw environment interactions.