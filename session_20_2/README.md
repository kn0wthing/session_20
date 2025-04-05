# Self-Driving Car Simulation

A Kivy-based simulation environment for training a self-driving car using reinforcement learning. The project implements a Deep Q-learning neural network that learns to navigate through a custom map while avoiding obstacles.

## Features

- Real-time simulation of a self-driving car
- Deep Q-Network (DQN) based reinforcement learning
- Interactive environment with customizable maps
- Three sensors for obstacle detection
- Dynamic goal-based navigation system with multiple target points
- Drawing tools to create custom obstacles
- Save/Load functionality for trained models
- Boundary handling to keep the car within the map

## Requirements

- Python 3.x
- PyTorch
- Kivy
- NumPy
- Matplotlib
- PIL (Python Imaging Library)

## Installation

Create a Python 3 virtual environment:
```bash
python3 -m venv venv

# Activate the virtual environment
# On Windows:
venv\Scripts\activate
# On macOS/Linux:
source venv/bin/activate

# Install required dependencies
pip install torch kivy numpy pillow matplotlib
```

## Project Structure

- `map.py` - Main simulation environment and game logic
- `ai.py` - Neural network architecture and Q-learning implementation
- `car.kv` - Kivy layout definitions for the UI
- `images/` - Contains map assets and masks
  - `car.png` - Car sprite
  - `mgroad_map_only_mask_base.png` - Base map mask for display
  - `mgroad_map_only_mask_hw.png` - Highway map mask for obstacle detection
- `last_brain.pth` - Saved neural network weights

## Map Configuration

The simulation uses a large map with dimensions:
- Width: 2876 pixels
- Height: 1250 pixels

The map is configured to match real-world road layouts, with:
- Black areas representing drivable roads
- Non-black areas representing obstacles or off-road terrain

## Usage

1. Run the simulation:
```bash
python map.py
```

2. Controls:
- The car moves automatically based on the AI
- Use the mouse to draw obstacles (left click and drag)
- Clear button: Removes all drawn obstacles
- Save button: Saves the current state of the AI
- Load button: Loads the previously saved AI state

## How It Works

### Car Sensors
- The car has three sensors:
  - Front sensor (straight ahead)
  - Right sensor (30° right of forward direction)
  - Left sensor (30° left of forward direction)
- Each sensor detects obstacles within a 20x20 pixel area
- Sensor signals range from 0 (no obstacles) to 1 (fully blocked)
- Boundary detection adds a value of 10 to indicate map edges

### Learning System
- Uses a Deep Q-Network (DQN) with:
  - 5 input neurons (3 sensors + 2 orientation values)
  - 3 possible actions (straight, right turn 5°, left turn 5°)
  - Reward system based on:
    - -2 reward for hitting obstacles or boundaries
    - +1 reward for reaching goals
    - +0.5 reward for moving closer to the goal
    - -0.1 small negative reward for regular movements

### Goals System
The car navigates between four predefined goals in sequence:
1. (504, 930)
2. (471, 50)
3. (1690, 550)
4. (2676, 380)

Each goal is marked by a red circle on the map, and the car automatically switches to the next goal when it comes within 25 pixels of the current goal.

### Car Behavior
- Normal speed: 3 units per frame on road
- Reduced speed: 1 unit per frame on obstacles
- The car reverses direction (180° turn) when it hits map boundaries
- Boundary checking keeps the car at least 20 pixels from the edge

## Neural Network Architecture
The DQN implementation in `ai.py` contains:
- Input layer: 5 neurons
- Hidden layers with ReLU activation
- Output layer: 3 neurons (representing possible actions)
- Experience replay for stable learning
- Adam optimizer with learning rate of 0.001

