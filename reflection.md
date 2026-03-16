# 💭 Reflection: Game Glitch Investigator

Answer each question in 3 to 5 sentences. Be specific and honest about what actually happened while you worked. This is about your process, not trying to sound perfect.

## 1. What was broken when you started?

- What did the game look like the first time you ran it?
The game looked largely normal and working the first time we ran the code. However, there were a few inconsistencies in some areas.

- List at least two concrete bugs you noticed at the start  
  (for example: "the secret number kept changing" or "the hints were backwards").
1. The number of attempts is not consistent within the page and this applies to all difficulty levels. For example, the game says we are given 8 attempts, but the middle of the page says 7 attempts, and stops taking answers after 6 attempts.
2. The message given when the input is not the secret number is the opposite of what is should be.
3. The new game button does not let us play a new game until we refresh the page.
---

## 2. How did you use AI as a teammate?

- Which AI tools did you use on this project (for example: ChatGPT, Gemini, Copilot)?
I used Claude Code on this project.

- Give one example of an AI suggestion that was correct (including what the AI suggested and how you verified the result).
When I asked Claude to change the location of the game logic methods, it successfully changed the location without changing the algorithm.

- Give one example of an AI suggestion that was incorrect or misleading (including what the AI suggested and how you verified the result).
There was no incorrect generations made by the AI, but it was also not the most efficient version it could be. I then had to manually change certain code parts to make it more efficient and decrease the number of lines of code. I verified each edit by going through the code and visualizing what it would do. I also tested it with the live version through streamlit.
---

## 3. Debugging and testing your fixes

- How did you decide whether a bug was really fixed?
I decided whether a bug was really fixed by seeing whether the change came through on the live version and the bug never appears again. Furthermore, I also made some test methods in the test_game_logic.py file to test the mothod so it returns what is expected.

- Describe at least one test you ran (manual or using pytest) and what it showed you about your code.
One test that I ran was the test on the check_guess() method with various inputs to see whether its output was what was expected. The tests ran and all passed, so my code runs without issues.

- Did AI help you design or understand any tests? How?
AI helped me write the general structure of the test, as well as making sure the test run on terminal. It made a conftest.py file in the overall project folder so pytest would run without issues.
---

## 4. What did you learn about Streamlit and state?

- In your own words, explain why the secret number kept changing in the original app.
The secret number kept changing in the original app because it was being generated at the top level of the script on every run. The secret code would change everytime the code "secret = random.randint(...)" ran, whether it was intentional or not.
- How would you explain Streamlit "reruns" and session state to a friend who has never used Streamlit?
Streamlit reruns the entire script whenever the user interacts with the app. To prevent values from resetting on each rerun, you can store them in st.session_state, which persists across reruns for a single user session. When you reload the entire page, then Streamlit assumes it is a new session, and resets all the session variables inside st.session_state.
- What change did you make that finally gave the game a stable secret number?
I initialized the secret number only if it didn’t already exist (or when starting a new game). This ensures that the secret number remains the same across all user interactions until the game is explicitly reset.
---

## 5. Looking ahead: your developer habits

- What is one habit or strategy from this project that you want to reuse in future labs or projects?
  - This could be a testing habit, a prompting strategy, or a way you used Git.
One habit from this proejct that I want to reuse in future projects is breaking down the logic into separate modules (like logic_utils.py) to keep the main script clean and easier to debug.
- What is one thing you would do differently next time you work with AI on a coding task?
One thing I would do differently next time I work with AI is spend more time verifying and understanding each AI-generated function before integrating it, rather than assuming it works correctly.
- In one or two sentences, describe how this project changed the way you think about AI generated code.
This project changed the way I think about AI Generated code because it showed me that AI can vastly accelerate development, but reviewing the edits is essential to catch subtle bugs and ensure the code behaves as intended.
