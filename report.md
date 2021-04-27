## Algorithm 

### General 

The method uses a DDPG algorithm. DDPG is an off-policy actor critic method for learning continious actions. The actor hereby takes the 33-dimensional state space (consisting of arm positions, accelerations, 
velocities and angles, ...) and outputs a single action. The critic network takes in the action and state and outputs a Q-value for the given inputs. In order to encourage
exploration, Ornstein-Uhlenbeck noise is added to the action. 
The actor is implemented as a target network, due to target networks decorrelating the process and generally improving performance. Soft updates are used in DDPG, which means 
that at every update step, the local networks are updated by a certain amount of the weights of the target networks according to a hyperparameter TAU (see below). 

### Loss Function 

### General 

### Loss


## Hyperparameters 

```python 
BUFFER_SIZE = int(1e5)  # replay buffer size
BATCH_SIZE = 128        # minibatch size
GAMMA = 0.99            # discount factor
TAU = 1e-3              # for soft update of target parameters
LR_ACTOR = 1e-3         # learning rate of the actor 
LR_CRITIC = 1e-3        # learning rate of the critic
WEIGHT_DECAY = 0        # L2 weight decay
```
Ornstein-Uhlenbeck parameters : 

```python 
mu = 0.5 
theta = 0.15
sigma = 0.2
```

## Possible Improvements 
