# Reinforcement-Learning-Example
Some little project about reinforcement learning, about how to setup and build an agent.
# Junia Racer
### Context
It's a simple 2D car game, with the aim of completing 3 laps as quickly as possible without touching the edges. If an edge is touched, the car starts again from the beginning, so you have to complete the 3 laps without colliding.

So, the project was given to me functional (the game) with movement using the keyboard arrows

### Solution

# MouseMaze
## No Random map
## Random map

# Snake
### Context
The aim of this project was to set up an agent on unity with ML-Agents. I had carte blanche on the choice of game and 2D or 3D. So I decided to go for a 2D game I've played a lot, SNAKE.
Nevertheless, I decided to use unity 3D for this, on version 2023.2.20f1.
### My solution
**First Step** : I remade the snake game, adding a floor, 4 walls, a head, an apple and the body in a prefab. Then in the code I defined the spawn of the head and the apple inside the walls and defined that if the head touches a wall then we respawn. and logically when the head eats an apple, I gain part of my body and if the head eats his body I die. I also look for the spawn of each object if the place is free. then created an empty gameobject “SnakeAgent”, to which I assign each element I defined earlier (apple/head/body/wall). For now, it moves randomly

**Second Step** : Setting up the ML-Agents environment, I imported the ML-Agents packages into unity, I assigned the "Decision Requester" and "Behavior Parameter" module, the first is therefore used to send a decision on the action that the agent must do (direction) and the second is used to define an agent to control my snake (in learning mode, I define none). and so then to finish on my side I change the movement operation which was on random and I say that we move only on the decisions of "Decision Requester"

**Third Step** :
### Reward
- If the snake eats the apple: +10
- If the snake moves closer to the apple: 0.01 / (distance2apple) + 1. So the closer the snake gets to the apple, the more reward it gets.
- If the snake runs into a wall: -1
- If the snake eats its own body: -5
### Result
![CleanShot 2025-02-27 at 10 03 41](https://github.com/user-attachments/assets/d0d9d4ef-fcb3-453c-8c66-70f7b8a0b5ed)

In the end, at the end of my training (1000000), the best score obtained was 15.
### Improvement
- adding rewards that increment when he eats an apple, the more he eats the more it pays off
- Add bigger penalties if the snake hits a wall or eats its own body.



