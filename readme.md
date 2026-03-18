# Quiz CLI

An interactive command-line quiz game for learning JavaScript, Node.js, and general programming concepts. This repository contains a small, beginner-friendly CLI app that demonstrates modern JavaScript (ES Modules), async/await, file system I/O, user input handling, and simple game logic.

---

## Features

- Multiple categories of questions (JavaScript, Node.js, General Programming)
- Select how many questions to answer (All / 3 / 5 when available)
- Shuffled questions each run
- Progress bar and per-question feedback
- Final results summary with review of incorrect answers and explanations
- Pure Node.js implementation with no external dependencies

---

## Demo

Run the app and follow prompts to:
1. Choose a category
2. Choose how many questions to answer
3. Select the numbered answer for each question
4. View your score and review incorrect answers

---

## Requirements

- Node.js >= 18.0.0 (uses native ES Modules and built-in promises APIs)
- Works on macOS, Linux, and Windows terminals that support ANSI colors

---

## Installation

1. Clone the repository:

   git clone <repo-url>
   cd test-app/test-app

2. (Optional) Install dependencies — this project has no production dependencies, but you can run npm install if you add any packages later:

   npm install

---

## Running the app

From the `test-app/test-app` directory, run:

   npm start

Or directly with node:

   node index.js

The CLI will clear the screen, display a banner, and prompt you to choose a category and the number of questions. Answer by entering the number corresponding to your choice.

---

## Project structure

- index.js — Entry point and main application loop
- package.json — Project metadata (name: quiz-cli, license: MIT)
- data/questions.json — Question database organized by category
- src/
  - input.js — User input helpers (readline wrappers: select, confirm, prompt)
  - quiz.js — Quiz game logic and results
  - colors.js — Lightweight ANSI color helpers for terminal output

There are also some macOS metadata files in the repository (__MACOSX/*) that can be ignored or removed.

---

## Data: Adding or Editing Questions

Questions are stored in JSON at `test-app/test-app/data/questions.json` using this shape:

  {
    "categories": {
      "categoryId": {
        "name": "Category Display Name",
        "questions": [
          {
            "question": "The question text",
            "options": ["opt A", "opt B", "opt C"],
            "answer": 0,              // index of correct option (0-based)
            "explanation": "Optional explanation shown after answering"
          }
        ]
      }
    }
  }

To add a new category, add a new object under `categories` with a unique key and supply a `name` and `questions` array.

---

## Development notes

- Uses ES Modules ("type": "module" in package.json)
- Readline-based input lives in src/input.js and returns Promises for cleaner async flow
- Quiz logic uses a Fisher-Yates shuffle to randomize questions
- The app is intentionally dependency-free to keep the example focused on core Node.js APIs

---

## Testing

There are no automated tests included. The package.json has a `test` script placeholder that runs `node --test`. You can add tests using Node's built-in test runner or a framework like Jest.

---

## Contributing

Contributions are welcome! Suggested ways to contribute:
- Add more questions and categories to `data/questions.json`
- Improve accessibility of prompts and input validation
- Add unit tests for the Quiz class and input helpers

Please open issues or PRs with clear descriptions.

---

## License

This project is licensed under the MIT License. See `package.json` for metadata.

---

## Contact

If you have questions about the code or want help extending the project, open an issue in this repository.

----

Happy learning! 🎓
