# Robotic Arm Navigation Project Reinforcement Learning Nanodegree 

## Project


We are working with the [Reacher](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Learning-Environment-Examples.md#reacher) environment. In this environment, a double-jointed arm can move to target locations. A reward of +0.1 is provided for each step that the agent's hand is in the goal location. Thus, the goal of the agent is to maintain its position at the target location for as many time steps as possible.The observation space consists of 33 variables corresponding to position, rotation, velocity, and angular velocities of the arm. Each action is a vector with four numbers, corresponding to torque applicable to two joints. Every entry in the action vector should be a number between -1 and 1. 

## Credits 

The ddpg code is adapted to the reacher task as used in the OpenAI pendulum exercise of the Nanodegree and provided in this [Subfolder](https://github.com/udacity/deep-reinforcement-learning/tree/master/ddpg-pendulum) of their Deep RL repo. 

Two simulations are provided for the enviornment : 
1) single agent enviornment 
2) twenty identical agents

For both possible enviornments, the goal is to get a score of +30 (over 100 consecutive episodes, and over all agents in the 20 agents case).


## Setup Instructions

### Python 

Setup your Python Enviornment according to the instructions by [Udacity](https://github.com/udacity/deep-reinforcement-learning#dependencies) (as shown below). This will install important frameworks like PyTorch and the ML-Agents toolkit.   

## Dependencies

To set up your python environment to run the code in this repository, follow the instructions below.

1. Create (and activate) a new environment with Python 3.6.

	- __Linux__ or __Mac__: 
	```bash
	conda create --name drlnd python=3.6
	source activate drlnd
	```
	- __Windows__: 
	```bash
	conda create --name drlnd python=3.6 
	activate drlnd
	```
	



## Unity Framework 

Select the file that corresponds to your operating system (see bewow).  
Then place the file in the DRLND GitHub repository, in the p1_navigation/ folder, and unzip (or decompress) the file.

1 Agent Version : 

- [Linux](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/one_agent/Reacher_Linux.zip)
- [MacOS](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/one_agent/Reacher.app.zip) 
- [Windows](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/one_agent/Reacher_Windows_x86_64.zip)

20 Agents Version : 

- [Linux](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher_Linux.zip)
- [MacOS](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher.app.zip)
- [Windows](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher_Windows_x86_64.zip)


Then, place the file in the p2_continuous-control/ folder in the DRLND GitHub repository, and unzip (or decompress) the file.

For AWS : If you'd like to train the agent on AWS (and have not [enabled a virtual screen](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Training-on-Amazon-Web-Service.md)), then please use [this link](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Training-on-Amazon-Web-Service.md) to obtain the environment.


## Instructions 
For running the code refer to the markdown comments in the Continious_Control.ipynb file. 

