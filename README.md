# Reinforcement-Learning-Example
Some little project about reinforcement learning, about how to setup and build an agent.
# Junia Racer
### Context
This is a 2D circuit car game in python, the objective is to move the car forward without colliding (which makes us start again), the objective of this project is to set up an agent who can do 3 laps as quickly as possible without colliding

So, the project was given to me functional (the game) with movement using the keyboard arrows, The car has 5 sensors in front of it, which send the distance from the walls, we also have information on the speed.

The overall goal is to set up an environment, when an agent can train. So in the end the goal of the agent is first to finish the circuit 3 times, and secondly to be as fast as possible

### My solution
**First Step** : I restructured the code to remove the manual movement with the arrows, I kept all the basic methods such as the sensors which return the distance in front of the car, the definition of the car with the acceleration, the turn, the circuit system, the reset, the collisions.

**Second Step** : I then set up a gymnasium environment in this code, in which I define everything the agent needs to know to learn. It is therefore in this environment that I put the map functions for the circuit with pygames, creation of the car, I also set up an observation space, this is a set of data that the agent receives and which allows it to make decisions on what it observes. In this observation space, I put the distance that I receive from the sensors in front. In the gymnasium environment I also put the reset function and the possible actions (forward, backward, left and right). And this is also where I set up my reward system.

**Third Step** : once my environment is defined, I set up my training and test file. So in this file I create an environment from the one I defined previously and with stable baselines 3 I define a PPO agent that will learn to play based on the rewards and observations it receives. I configure 100000 epoch, and I save the result, which I reuse in my test file to visualize the result.
### Reward
- If the car has a collision: -1000
- If the car turns around: -50
- If the car stays on the track: +10
- If the car moves forward, reward based on speed, so the faster the car goes, the bigger the reward. Otherwise -1 (because the car stays in place)
- If the car brakes: -0.5
- If the car drives at a suitable speed: +10 (to prevent the car from driving as fast as possible to have a big reward even if it hits a wall)
### Result
**First race**

<img src="https://github.com/user-attachments/assets/84ef69da-e672-4fd8-9997-ea35f2641f32" alt="CleanShot 2025-02-27 at 11 12 25" width="500" height="300">



**Second race**

<img src="https://github.com/user-attachments/assets/5c00dbda-a328-4a61-b19b-d41401e02da4" alt="CleanShot 2025-02-27 at 11 07 04" width="500" height="300">


**Third race**

<img src="https://github.com/user-attachments/assets/7393f64c-978d-4aef-9178-bd1ac1a57445" alt="CleanShot 2025-02-27 at 11 15 09" width="500" height="300">


So at the end of my training (100000), my average time on each circuit is 14s


### Improvement

# MouseMaze
## No Random map
### Context
### My solution
### Reward
### Result
<img src="https://github.com/user-attachments/assets/c5dd3109-67f2-4f96-b4b2-5ff0f12a2211" alt="CleanShot 2025-02-27 at 11 22 06" width="300" height="300">

### Improvement


## Random map
### Context
### My solution
### Reward
### Result
### Improvement

# Snake
### Context
The aim of this project was to set up an agent on unity with ML-Agents. I had free rein on the choice of game and whether it should be 2D or 3D. So I decided to recreate a 2D game I played a lot: SNAKE.
However, I chose to use Unity 3D for this project, specifically version 2023.2.20f1.
### My solution
**First Step** : I recreated the Snake game by adding a floor, four walls, a snake head, an apple, and a body prefab. In the code, I implemented logic to spawn the snake's head and the apple inside the walls. I also ensured that if the snake's head touches a wall, the game resets. And logically when the head eats an apple, I gain part of my body and if the head eats his body I die. I also ensure that objects spawn in unoccupied spaces. then created an empty gameobject “SnakeAgent”, to which I assign each element I defined earlier (apple/head/body/wall). At this stage, the snake moves randomly.

**Second Step** : To set up the ML-Agents environment, I imported the ML-Agents package into Unity, I assigned the "Decision Requester" and "Behavior Parameter" module to "SnakeAgent", The first is responsible for requesting decisions on the agent’s actions (movement direction) and The second defines the behavior of the agent controlling the snake (in learning mode, I set it to 'None'). Finally, I replaced the random movement logic with actions dictated by the 'Decision Requester'.

**Third Step** : I set up the reward system, added a timer and a high score display, and duplicated the game environment to speed up training. Then, I launched the training using the command "mlagents-learn config/snake_config.yaml --run-id=snake --train #to train an agent "snake" is the name of this one" while running the game in Unity.

<img src="https://github.com/user-attachments/assets/d787070d-1cb5-4161-b098-cd50315677fe" alt="CleanShot 2025-02-27 at 11 10 48@2x" width="200" height="300">


### Reward
- If the snake eats the apple: +10
- If the snake moves closer to the apple, it receives a small reward based on the formula: 0.01/(distanceToApple+1). This encourages the agent to approach the apple efficiently. So the closer the snake gets to the apple, the more reward it gets.
- If the snake runs into a wall: -1
- If the snake eats its own body: -5
### Result
![CleanShot 2025-02-27 at 10 03 41](https://github.com/user-attachments/assets/d0d9d4ef-fcb3-453c-8c66-70f7b8a0b5ed)

In the end, at the end of my training (1000000), the best score obtained was 15.
### Improvement
- Adding incremental rewards when the snake eats an apple, making each apple more valuable as the game progresses.
- Increasing penalties when the snake hits a wall or eats its own body, to discourage reckless movement.



