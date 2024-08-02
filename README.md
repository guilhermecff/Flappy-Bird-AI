# Flappy Bird with NEAT Neural Networks

This project implements the classic game of Flappy Bird using Python and Pygame. It features an AI-powered gameplay using NEAT (NeuroEvolution of Augmenting Topologies) to train neural networks that can play the game autonomously. The project focuses on applying evolutionary algorithms to improve the performance of neural networks in the Flappy Bird game environment.

## Project Overview

- **Game:** Flappy Bird
- **Language:** Python
- **Libraries:** Pygame, NEAT-Python
- **Features:**
  - Pixel-perfect collision detection using masks
  - AI training using NEAT to evolve neural networks
  - Animated sprites and scrolling backgrounds

## Game Mechanics

Flappy Bird is a side-scrolling game where the player controls a bird, attempting to fly between columns of green pipes without hitting them. The player scores a point each time they pass through a pair of pipes.

## Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/guilhermecff/flappy-bird-AI.git
   cd flappy-bird-AI
   ```

2. **Install requirements**
   ```bash
   pip install requirements.txt
   ```

3. **Run**
  ```bash
    python flappy_bird.py
  ```


## Neural Network and AI Training

The game uses the NEAT (NeuroEvolution of Augmenting Topologies) algorithm to evolve neural networks capable of playing Flappy Bird. Here is a breakdown of how the neural network is structured and trained:

### NEAT Algorithm

NEAT is a genetic algorithm that evolves neural networks over generations. It starts with a simple network and complexifies it by adding neurons and connections. This approach allows it to find innovative solutions to problems by evolving both the topology and weights of neural networks.

### Neural Network Architecture

Each bird (agent) is controlled by a neural network that takes the following inputs:

- The bird's vertical position (`bird.y`)
- The distance between the bird and the top pipe (`abs(bird.y - pipes[pipe_ind].height)`)
- The distance between the bird and the bottom pipe (`abs(bird.y - pipes[pipe_ind].bottom)`)

The network outputs a single value that determines whether the bird should jump or not.

### Fitness Function

The fitness function is designed to reward birds that survive longer and pass through pipes. The main components of the fitness function are:

- **Time Alive:** Each frame a bird stays alive, it receives a small fitness increment (`0.1`).
- **Pipe Passed:** When a bird successfully passes through a pipe, it receives a significant fitness bonus (`5`).

### Training Process

1. **Population Initialization:** The NEAT algorithm initializes a population of neural networks (birds).
2. **Simulation:** Each bird plays the game using its neural network to decide jumps.
3. **Evaluation:** Birds are evaluated based on their fitness scores.
4. **Selection and Mutation:** The best-performing networks are selected, and genetic operations (crossover and mutation) are applied to create a new generation.
5. **Repeat:** The process is repeated for a specified number of generations or until a satisfactory performance level is achieved.

### Configuration

The NEAT algorithm is configured using a `config.txt` file that specifies parameters such as population size, mutation rates, and species settings.

## Game Development

### Classes

- **Bird:** Represents the player's bird and handles movement, jumping, and collision detection.
- **Pipe:** Represents obstacles in the game and handles their movement and collision logic.
- **Base:** Represents the ground in the game and handles its scrolling logic.
- **Neat-Python:** Manages the evolution of the neural networks.

### Collision Detection

The game uses pixel-perfect collision detection with masks to ensure precise interactions between the bird and pipes.

