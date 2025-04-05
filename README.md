# Reinforcement Learning Projects

This repository contains two reinforcement learning projects exploring different aspects of machine learning for autonomous agents.

## Project 1: Berkeley Pacman Reinforcement Learning

**Directory:** `session_20_1/`

A comprehensive suite of reinforcement learning implementations based on the Berkeley CS188 course, featuring:

- **Q-Learning**: Implementation of Q-learning algorithms for Pacman and Gridworld
- **Value Iteration**: Solving MDPs through value iteration approaches
- **Feature-based Q-Learning**: Advanced learning with feature extractors
- **Approximate Q-Learning**: Using function approximation for complex environments
- **Exploration Strategies**: Various exploration policies including ε-greedy

**Key Components:**
- `qlearningAgents.py`: Contains Q-learning agents implementation
- `valueIterationAgents.py`: Value iteration algorithm implementations
- `featureExtractors.py`: Feature extraction for approximate methods
- `gridworld.py`: Gridworld environment implementation
- `pacman.py`: Pacman game environment
- `crawler.py`: Robot crawler environment for learning movement

**Languages/Technologies:**
- Python
- Numpy for mathematical operations
- Tkinter for visualization

## Project 2: Self-Driving Car Simulation

**Directory:** `session_20_2/`

A Kivy-based simulation environment for training a self-driving car using Deep Q-Learning. The car learns to navigate between multiple target points while avoiding obstacles.

**Key Features:**
- Deep Q-Network (DQN) based reinforcement learning
- Interactive environment with customizable maps
- Three-sensor obstacle detection system
- Dynamic goal-based navigation between multiple targets
- Drawing tools to create custom obstacles

**Key Components:**
- `map.py`: Main simulation environment and game logic
- `ai.py`: Neural network architecture and Q-learning implementation
- `car.kv`: Kivy layout definitions for the UI
- `images/`: Contains map assets and masks for obstacle detection

**Languages/Technologies:**
- Python 3
- PyTorch for neural network implementation
- Kivy for interactive graphics
- NumPy for mathematical operations
- PIL for image processing

## Getting Started

### Prerequisites

- Python 3.x
- PyTorch (for Project 2)
- Kivy (for Project 2)
- NumPy
- Matplotlib (for Project 2)
- PIL (for Project 2)

### Installation

```bash
# Create a Python 3 virtual environment
python3 -m venv venv

# Activate the virtual environment
# On Windows:
venv\Scripts\activate
# On macOS/Linux:
source venv/bin/activate

# Install required dependencies
pip install torch kivy numpy pillow matplotlib
```

## Running the Projects

### Project 1: Berkeley Pacman

```bash
cd session_20_1

# Run Gridworld with value iteration
python gridworld.py -a value -i 100 -k 10

# Run Q-learning on Gridworld
python gridworld.py -a q -k 100

# Run Pacman with Q-learning
python pacman.py -p QLearnAgent -x 2000 -n 2010 -l smallGrid
```

### Project 2: Self-Driving Car

```bash
cd session_20_2

# Run the self-driving car simulation
python map.py
```

## Learning Goals

These projects demonstrate various reinforcement learning concepts:

1. **Value Functions**: Learning state and action values
2. **Policy Learning**: Discovering optimal policies for navigation
3. **Exploration vs. Exploitation**: Balancing discovery and optimization
4. **Neural Networks in RL**: Using deep learning for complex environments
5. **Interactive Learning**: Real-time visualization of learning progress
