# Tic-Tac-Toe with Gradient Circle

This project combines a simple Tic-Tac-Toe web application with a visually appealing gradient circle using HTML, CSS, and JavaScript.

### Description

This is an engaging Tic Tac Toe game implemented using HTML, CSS, and JavaScript. The game features a 3x3 grid where two players take turns to mark their symbols (X and O) with the goal of placing three of their marks in a row, whether horizontally, vertically, or diagonally. The interface is designed with custom fonts and vibrant colors to enhance visual appeal and make the game enjoyable to play.


## Features

- Two-player game: Alternates between X and O players.
- Winning detection: Highlights the winning combination
- Restart button: Resets the game to play again.
- Stylish design: Uses custom fonts and colors for a better visual experience.

## Technologies Used

- HTML
- CSS
- JavaScript

## Installation

1. Clone the repository or download the code.
2. Open the Tic Tac Toe.html file in your web browser.

## Usage

1. Open the Tic Tac Toe.html file in a web browser.
2. Players take turns clicking on the grid to place their marks
3. The first player to align three of their marks in a row wins.
4. Click the "Restart" button to reset the game board.


## Code Overview

 ### HTML

 The HTML structure includes a container for the game title, the game board, and a restart button.

### CSS 

The CSS styles define the visual appearance, including the grid layout, font styles, colors, and responsive design adjustments.

## Javascript 

The JavaScript code handles the game logic :

- Initializes the game board and player turns.
- Detects player moves and updates the game state.
- Checks for winning conditions and highlights the winning combination.
- Resets the game board when the restart button is clicked.

```javascript

let playerText = document.getElementById('playerText');
let restartBtn = document.getElementById('restartBtn');
let boxes = Array.from(document.getElementsByClassName('box'));

let winnerIndicator = getComputedStyle(document.body).getPropertyValue('--winning-blocks');

const O_TEXT = "O";
const X_TEXT = "X";
let currentPlayer = X_TEXT;
let spaces = Array(9).fill(null);

const startGame = () => {
    boxes.forEach(box => box.addEventListener('click', boxClicked));
}

function boxClicked(e) {
    const id = e.target.id;

    if (!spaces[id]) {
        spaces[id] = currentPlayer;
        e.target.innerText = currentPlayer;

        if (playerHasWon() !== false) {
            playerText.innerHTML = `${currentPlayer} has won!`;
            let winning_blocks = playerHasWon();

            winning_blocks.map(box => boxes[box].style.backgroundColor = winnerIndicator);
            return;
        }

        currentPlayer = currentPlayer == X_TEXT ? O_TEXT : X_TEXT;
    }
}

const winningCombos = [
    [0, 1, 2],
    [3, 4, 5],
    [6, 7, 8],
    [0, 3, 6],
    [1, 4, 7],
    [2, 5, 8],
    [0, 4, 8],
    [2, 4, 6]
];

function playerHasWon() {
    for (const condition of winningCombos) {
        let [a, b, c] = condition;

        if (spaces[a] && (spaces[a] == spaces[b] && spaces[a] == spaces[c])) {
            return [a, b, c];
        }
    }
    return false;
}

restartBtn.addEventListener('click', restart);

function restart() {
    spaces.fill(null);

    boxes.forEach(box => {
        box.innerText = '';
        box.style.backgroundColor = '';
    });

    playerText.innerHTML = 'Tic Tac Toe';

    currentPlayer = X_TEXT;
}

startGame();

```

## Contact

For any furter queries kindly contact on :

 Email : Narayanbaheti13@gmai.com
