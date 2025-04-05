# Reinforcement Learning Agents Implementation

## Acknowledgments

This project adapts the Reinforcement Learning assignment from UC Berkeley's CS188: Introduction to Artificial Intelligence course. Access the original assignment at [ai.berkeley.edu/reinforcement.html](https://ai.berkeley.edu/reinforcement.html).

The Pacman AI projects were created at UC Berkeley, with primary development by John DeNero (denero@cs.berkeley.edu) and Dan Klein (klein@cs.berkeley.edu). Student-facing autograding functionality was contributed by Brad Miller, Nick Hay, and Pieter Abbeel (pabbeel@cs.berkeley.edu).

This implementation features two reinforcement learning agent types for the Pacman environment:
1. Q-Learning Agent
2. Value Iteration Agent

## Q-Learning Agent Implementation

The `QLearningAgent` class employs the Q-learning algorithm to discover optimal actions through experiential learning. Key implemented components include:

### Core Functions

1. `__init__(self, **args)`
   - Sets up the Q-learning agent
   - Establishes a Counter object for Q-value storage
   - Acquires parameters from ReinforcementAgent (epsilon, alpha, discount)

2. `getQValue(self, state, action)`
   - Retrieves the Q-value for a specific state-action pair
   - Provides 0.0 for previously unseen state-action combinations
   - Utilizes a Counter data structure for optimized storage and retrieval

3. `computeValueFromQValues(self, state)`
   - Calculates the highest Q-value across all available actions in a state
   - Yields 0.0 when no legal actions exist (terminal state)
   - Supports value estimation and policy enhancement

4. `computeActionFromQValues(self, state)`
   - Identifies the optimal action for a given state
   - Returns None for terminal states or states without legal actions
   - Leverages Q-values to determine the best action

5. `getAction(self, state)`
   - Implements an epsilon-greedy selection strategy
   - Explores with random actions (probability epsilon)
   - Exploits with optimal actions (probability 1-epsilon)
   - Returns None for terminal states

6. `update(self, state, action, nextState, reward)`
   - Refreshes Q-values using the Q-learning equation:
     Q(s,a) = (1-α)Q(s,a) + α(r + γmax_a'Q(s',a'))
   - α (alpha): learning rate parameter
   - γ (gamma): discount factor parameter
   - r: obtained reward

## Value Iteration Agent Implementation

The `ValueIterationAgent` class implements value iteration to compute optimal values and policies directly from the MDP model. Key implemented components include:

### Core Functions

1. `__init__(self, mdp, discount=0.9, iterations=100)`
   - Initializes the value iteration agent
   - Executes value iteration for the specified iteration count
   - Applies the Bellman equation for optimal value computation:
     V(s) = max_a Σ P(s'|s,a)[R(s,a,s') + γV(s')]

2. `computeQValueFromValues(self, state, action)`
   - Derives Q-values from the value function
   - Applies the formula: Q(s,a) = Σ P(s'|s,a)[R(s,a,s') + γV(s')]
   - Accounts for all potential successor states and their transition probabilities

3. `computeActionFromValues(self, state)`
   - Selects the best action based on the computed value function
   - Returns None for terminal states or states without legal actions
   - Uses Q-values to identify the optimal action choice

### Key Differences

1. **Learning Approach**:
   - Q-Learning: Acquires knowledge through experience (model-free approach)
   - Value Iteration: Directly calculates optimal values from the MDP (model-based approach)

2. **Update Process**:
   - Q-Learning: Updates Q-values incrementally after each action
   - Value Iteration: Pre-calculates all values before taking any action

3. **Exploration**:
   - Q-Learning: Employs epsilon-greedy exploration strategy
   - Value Iteration: No exploration mechanism (consistently selects optimal actions)

## Virtual Environment Setup

This project uses Python 2, which is no longer supported in newer systems. To set up a compatible environment:

```bash
# Install virtualenv if you don't have it (one-time setup)
pip install virtualenv

# Create a Python 2 virtual environment
virtualenv -p python2 venv_py2

# Activate the virtual environment
# On Windows:
venv_py2\Scripts\activate
# On macOS/Linux:
source venv_py2/bin/activate

# Install required dependencies
pip install -r requirements.txt
```

All Python commands should be run within this activated Python 2 virtual environment.

## Usage

To utilize these agents in the Pacman environment (make sure your virtual environment is activated):

```bash
# For Q-Learning Agent
# For Value Iteration Agent
python pacman.py -p ValueIterationAgent -a discount=0.9,iterations=100
```

## Parameters

### Q-Learning Agent
- `epsilon`: Exploration probability (default: 0.05)
- `alpha`: Learning rate (default: 0.2)
- `gamma`: Discount factor (default: 0.8)

### Value Iteration Agent
- `discount`: Discount factor (default: 0.9)
- `iterations`: Number of value iteration iterations (default: 100)

## Screen Outputs

### Sample output
<img src="images\output2.jpg" width="800" alt="Q-Learning Agent Output">

Terminal

<img src="images\output3.jpg" width="800" alt="Q-Learning Agent Output">
