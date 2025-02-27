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
### My solution
### Reward
- If the snake eats the apple: +10
- If the snake moves closer to the apple: 0.01 / (distance2apple) + 1. So the closer the snake gets to the apple, the more reward it gets.
- If the snake runs into a wall: -1
- If the snake eats its own body: -5
### Result
![CleanShot 2025-02-27 at 10 03 41](https://github.com/user-attachments/assets/d0d9d4ef-fcb3-453c-8c66-70f7b8a0b5ed)

In the end, at the end of my training (1000000), the best score obtained was 15.



