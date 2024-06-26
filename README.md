# Guess My Number!

Welcome to the "Guess My Number!" game! This project is a simple number guessing game developed using HTML, CSS, and JavaScript. The game is designed to be fully responsive and works seamlessly on desktop, tablet, and mobile devices.

## Game Rules

"Guess My Number!" is a game where players try to guess a randomly generated number between 1 and 20. Here are the detailed rules:

1. **Starting the Game:**
   - The game randomly generates a secret number between 1 and 20 at the start.
   - The player's initial score is set to 20.

2. **Making a Guess:**
   - The player enters their guess in the input field and clicks the "Check!" button.
   - The game will provide feedback:
     - "⛔️ No number!" if the input field is empty.
     - "🎉 Correct Number!" if the guess is correct, and the secret number is revealed.
     - "Too high!" if the guess is higher than the secret number.
     - "Too low!" if the guess is lower than the secret number.

3. **Scoring:**
   - For each incorrect guess, the player's score decreases by 1.
   - The game ends when the player's score reaches 0, displaying "💥 You lost the game!".
   - If the player guesses correctly, the game checks if the current score is higher than the highscore and updates it accordingly.

4. **Restarting the Game:**
   - The player can click the "Again!" button to reset the game with a new secret number and reset the score to 20.

## How to Play

1. **Start a New Game:**
   - Open the game in your browser. The game will automatically start with a secret number between 1 and 20.

2. **Make a Guess:**
   - Enter a number between 1 and 20 in the input field and click the "Check!" button.
   - The game will provide feedback and update the score based on your guess.

3. **Restart the Game:**
   - Click the "Again!" button to reset the game and start over with a new secret number and a score of 20.

## Technologies Used

- **HTML**: For the game structure.
- **CSS**: For styling the game, including responsive design for different devices.
- **JavaScript**: For the game logic, including number generation, score tracking, and game state management.

## Features

- **Responsive Design**: The game layout adjusts seamlessly for desktop, tablet, and mobile devices.
- **Interactive UI**: Real-time updates to the feedback messages, score, and highscore.
- **Simple and Intuitive Gameplay**: Easy to understand and play, with clear rules and controls.

## Installation and Setup

To run this game locally on your machine, follow these steps:

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/yourusername/guess-my-number.git
   ```

2. **Navigate to the Project Directory:**
   ```bash
   cd guess-my-number
   ```

3. **Open `index.html` in your browser:**
   - You can open the `index.html` file directly in your preferred web browser.

## Contribution

If you want to contribute to this project, feel free to fork the repository and submit a pull request. Your contributions are always welcome!

## Contact

For any questions or suggestions, please feel free to contact me at your.email@example.com.

---

### Example Code Snippets

**HTML:**
```html
<header>
  <h1>Guess My Number!</h1>
  <p class="between">(Between 1 and 20)</p>
  <button class="btn again">Again!</button>
  <div class="number">?</div>
</header>
<main>
  <section class="left">
    <input type="number" class="guess" />
    <button class="btn check">Check!</button>
  </section>
  <section class="right">
    <p class="message">Start guessing...</p>
    <p class="label-score">💯 Score: <span class="score">20</span></p>
    <p class="label-highscore">
      🥇 Highscore: <span class="highscore">0</span>
    </p>
  </section>
</main>
```

**CSS:**
```css
body {
  font-family: 'Press Start 2P', sans-serif;
  color: #eee;
  background-color: #222;
}

header {
  position: relative;
  height: 35vh;
  border-bottom: 7px solid #eee;
}

main {
  height: 65vh;
  display: flex;
  align-items: center;
  justify-content: space-around;
}

.number {
  background: #eee;
  color: #333;
  font-size: 6rem;
  width: 15rem;
  padding: 3rem 0;
  text-align: center;
  position: absolute;
  bottom: 0;
  left: 50%;
  transform: translate(-50%, 50%);
}

.guess {
  background: none;
  border: 4px solid #eee;
  font-family: inherit;
  color: inherit;
  font-size: 5rem;
  padding: 2.5rem;
  width: 25rem;
  text-align: center;
  display: block;
  margin-bottom: 3rem;
}

.btn {
  border: none;
  background-color: #eee;
  color: #222;
  font-size: 2rem;
  font-family: inherit;
  padding: 2rem 3rem;
  cursor: pointer;
}
```

**JavaScript:**
```javascript
'use strict';

let secretNumber = Math.trunc(Math.random() * 20) + 1;
let score = 20;
let highscore = 0;

const displayMessage = function (message) {
  document.querySelector('.message').textContent = message;
};

document.querySelector('.check').addEventListener('click', function () {
  const guess = Number(document.querySelector('.guess').value);

  if (!guess) {
    displayMessage('⛔️ No number!');
  } else if (guess === secretNumber) {
    displayMessage('🎉 Correct Number!');
    document.querySelector('.number').textContent = secretNumber;
    document.querySelector('body').style.backgroundColor = '#3ca49d';
    document.querySelector('.number').style.width = '30rem';

    if (score > highscore) {
      highscore = score;
      document.querySelector('.highscore').textContent = highscore;
    }
  } else if (guess !== secretNumber) {
    if (score > 1) {
      displayMessage(guess > secretNumber ? 'Too high!' : 'Too low!');
      score--;
      document.querySelector('.score').textContent = score;
    } else {
      displayMessage('💥 You lost the game!');
      document.querySelector('.score').textContent = 0;
    }
  }
});

document.querySelector('.again').addEventListener('click', function () {
  score = 20;
  secretNumber = Math.trunc(Math.random() * 20) + 1;

  displayMessage('Start guessing...');
  document.querySelector('.score').textContent = score;
  document.querySelector('.number').textContent = '?';
  document.querySelector('.guess').value = '';
  document.querySelector('body').style.backgroundColor = '#222';
  document.querySelector('.number').style.width = '15rem';
});
