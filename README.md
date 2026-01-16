# Tic Tac Toe on STM32H750B-DK

This project implements a **Tic Tac Toe game** on the STM32H750B Discovery board using the LCD touchscreen for the game board, LEDs to indicate player turns and game status, and a push-button for resetting the game.

## Features
- Touchscreen interface for placing X and O symbols
- LED indicators for Player X, Player O, and game-over status
- Push-button to reset the game using interrupts
- Game logic handles winner checking and turn management

## Implementation Details
- **Screen & Touch Input:** Used `stm32_lcd.h` library to draw grid, text, and read touch positions
- **LED Control:** Three GPIO pins configured as outputs
    - PI13: Player X LED
    - PJ2: Player O LED
    - PD3: Game over LED
- **Interrupts:** USER push-button uses HAL callback (`HAL_GPIO_EXTI_Callback`) to reset the game
- **Game Logic:** Functions include `CheckWinner()`, `DrawBoard()`, `HandleTouchInput()`, and `ResetGame()`

## Main Program Flow
1. Initialize HAL, system clock, LCD, touchscreen, LEDs, and push-button interrupt
2. Draw empty Tic Tac Toe board
3. Player X starts (LED on)
4. Players play via touchscreen input
5. Game checks for a winner and updates LEDs
6. Pressing the push-button resets the game

## Future Improvements
- Single-player mode vs CPU using the Minimax algorithm
- Score tracking across rounds

 ## Demo
   Watch the project in action: [Demo Video](https://youtu.be/icizZNqt9IU)

## Code Snippets
```c
void LED_SetTurn(int player) { ... }
void LED_GameOver(void) { ... }
int CheckWinner(void) { ... }
void ResetGame(void) { ... }
