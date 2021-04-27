## Algorithm 

### General 

The method uses a DDPG algorithm. DDPG is an off-policy actor critic method for learning continious actions. The actor hereby takes the 33-dimensional state space (consisting of arm positions, accelerations, 
velocities and angles, ...) and outputs a single action. The critic network takes in the action and state and outputs a Q-value for the given inputs. In order to encourage
exploration, Ornstein-Uhlenbeck noise is added to the action. 
The actor is implemented as a target network, due to target networks decorrelating the process and generally improving performance. Soft updates are used in DDPG, which means 
that at every update step, the local networks are updated by a certain amount of the weights of the target networks according to a hyperparameter TAU (see below). 

DDPG also uses experience replay to stabilize the training process, in the case of multi agents every single agent has its own replay buffer that only the agent can read from and write to. 

### Loss  

The critic loss is analogous to a DQN loss and is simply the mean squared error between the targets of the current state (calculated by the target network) and the 
output of the local network : 

```python 
critic_loss = F.mse_loss(Q_expected, Q_targets)
```


The actor is updated by backpropagating the error that is evaluated by calculating the average of q-values for each state/action pair as output by the critic network. 

```python 
actor_loss = -self.critic_local(states, actions_pred).mean()
```

### Networks 

Both the actor and critic networks are very simple feed forward networks with 2 hidden layers with ReLu activations of size 400 and 300 respectively. 
Since the critic outputs a Q-value, it does not have an activation function in the final layer. Compared to that, the actor uses a tanh function at the output to output a continious action in the range of [-1,1] for each of the 4 actions (torque that is sent to each joint). 

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

- [GAE](https://arxiv.org/abs/1506.02438) : combats the bias/variance tradeoff of TD estimates by introducing a hyperparameter lambda that allow to combine monte-carlo and TD estimates
- [Q-PROP](https://arxiv.org/abs/1611.02247): uses a Taylor Expansion to control the bias/variance tradeoff in off-policy methods 
- The batch algorithms TNPG and TRPO (TRPO enables faster learning through larger batch sizes) as suggested by the paper [Benchmarking Deep Reinforcement Learning for Continuous Control](https://arxiv.org/abs/1604.06778)
- Recurrent versions of the used method as suggested by [Benchmarking Deep Reinforcement Learning for Continuous Control](https://arxiv.org/abs/1604.06778), but that may make it more difficult to train 

