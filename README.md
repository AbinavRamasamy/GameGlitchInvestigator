# 🎮 Game Glitch Investigator: The Impossible Guesser

## 🚨 The Situation

You asked an AI to build a simple "Number Guessing Game" using Streamlit.
It wrote the code, ran away, and now the game is unplayable. 

- You can't win.
- The hints lie to you.
- The secret number seems to have commitment issues.

## 🛠️ Setup

1. Install dependencies: `pip install -r requirements.txt`
2. Run the broken app: `python -m streamlit run app.py`

## 🕵️‍♂️ Your Mission

1. **Play the game.** Open the "Developer Debug Info" tab in the app to see the secret number. Try to win.
2. **Find the State Bug.** Why does the secret number change every time you click "Submit"? Ask ChatGPT: *"How do I keep a variable from resetting in Streamlit when I click a button?"*
3. **Fix the Logic.** The hints ("Higher/Lower") are wrong. Fix them.
4. **Refactor & Test.** - Move the logic into `logic_utils.py`.
   - Run `pytest` in your terminal.
   - Keep fixing until all tests pass!

## 📝 Document Your Experience

- The game's purpose was to get us accustomed to coding with AI rather than let AI do everything. The overall function of the game was a number guesser where the computer chooses a number and the player tries ot guess the chosen number.
- When I first ran the game, I noticed several issues:
	1.	Inconsistent attempt counter: The number of attempts shown on the page did not match the actual number allowed. For example, the game stated that the player had 8 attempts, another part of the page displayed 7 attempts, and the game stopped accepting guesses after 6 attempts.
	2.	Incorrect hint messages: When a guess was not equal to the secret number, the hint message was reversed: if the guess was higher than the secret number, the game would incorrectly say the guess was too low, and vice versa.
	3.	New game button not functioning properly: The New Game button did not reset the game state. After finishing a game, clicking the button would not start a new round unless the page was manually refreshed.
- To resolve these issues, I made several changes to the code.
	1.	Fixed the attempt counter logic: I located where the attempt counter was defined and where it was displayed in the interface. I updated the logic so that the same variable controlled both the displayed number of attempts and the actual limit used in the game logic.
	2.	Corrected the hint conditions: I reviewed the conditional statements in the check_guess() method. The comparison operators were reversed, so I swapped the conditions to ensure that the message is correct.
	3.	Implemented proper game reset behavior: I modified the logic behind the New Game button and the difficulty selection, so it resets the game state variables. This ensures the game starts a fresh round without requiring the page to refresh.


## 📸 Demo

![Project Screenshot](./assets/screenshot.png)

<!-- ## 🚀 Stretch Features

- [ ] [If you choose to complete Challenge 4, insert a screenshot of your Enhanced Game UI here] -->
