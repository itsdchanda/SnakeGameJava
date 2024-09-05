
# Java Snake Game

## Overview
The **Java Snake Game** is a classic arcade-style game where the player controls a snake that moves around the board, eating food, and growing longer as a result. The goal is to grow the snake as long as possible without hitting the walls or itself. The game has basic graphics and uses keyboard controls for gameplay. It features game-over detection and the ability to reset the game with a simple keypress.

## Features
- **Simple gameplay mechanics:** Use arrow keys to control the snake’s direction.
- **Food consumption:** When the snake eats food, it grows longer, and the player’s score increases.
- **Collision detection:** The game ends if the snake runs into the walls or itself.
- **Reset option:** After the game ends, press 'R' to restart.
- **Score display:** The current score is displayed on the screen, showing the length of the snake.

## Game Rules
- Use the arrow keys (`↑`, `↓`, `←`, `→`) to move the snake.
- The snake will grow longer every time it eats the food, which is randomly placed on the game board.
- The game ends if the snake collides with the walls or its own body.
- After the game ends, press `R` to restart the game.

## Controls
- **Arrow Keys:** Control the movement of the snake.
- **R Key:** Restart the game when it's over.

## How to Run the Game
1. Clone the repository using the following command:
    ```bash
    git clone https://github.com/yourusername/JavaSnakeGame.git
    ```
2. Open the project in your favorite Java IDE (e.g., IntelliJ IDEA, Eclipse).
3. Compile and run the `SnakeGame` class.
4. Enjoy the game!

## Code Snippets

### Main Game Logic

```java
public void move() {
    // eat food
    if (collision(snakeHead, food)) {
        snakeBody.add(new Tile(food.x, food.y));
        placeFood();
    }

    // Snake Body
    for (int i = snakeBody.size() - 1; i >= 0; i--) {
        Tile snakePart = snakeBody.get(i);
        if (i == 0) {
            snakePart.x = snakeHead.x;
            snakePart.y = snakeHead.y;
        } else {
            Tile prevSnakePart = snakeBody.get(i - 1);
            snakePart.x = prevSnakePart.x;
            snakePart.y = prevSnakePart.y;
        }
    }

    // Snake Head
    snakeHead.x += velocityX;
    snakeHead.y += velocityY;

    // Game over conditions
    for (Tile snakePart : snakeBody) {
        if (collision(snakeHead, snakePart)) {
            gameOver = true;
        }
    }
    if (snakeHead.x * tileSize < 0 || snakeHead.x * tileSize >= boardWidth || snakeHead.y * tileSize < 0
            || snakeHead.y * tileSize >= boardHeight) {
        gameOver = true;
    }
}
```

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
