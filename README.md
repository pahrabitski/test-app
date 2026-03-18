# Quiz CLI

A small, dependency-free command-line quiz application written in Node.js. It provides interactive quizzes across multiple categories (JavaScript, Node.js, General Programming), shuffles questions each run, shows progress and per-question feedback, and gives a final summary with explanations for incorrect answers.

This README describes how to set up, run, and contribute to the project.

---

## Features

- Multiple question categories (e.g. JavaScript, Node.js, General Programming)
- Choose how many questions to attempt (All / 3 / 5 where available)
- Questions are shuffled each run (Fisher–Yates)
- Interactive CLI with per-question feedback and a final summary
- Review incorrect answers with explanations
- No external dependencies — pure Node.js (ES modules)

---

## Requirements

- Node.js >= 18.0.0 (uses modern Node APIs and ES modules)
- Unix-like terminal or Windows terminal that supports ANSI colors

The project is configured as an ES module project (`"type": "module"` in package.json). The CLI entry point includes a shebang, so it can be run directly after making it executable.

---

## Quick start

Clone the repository and run the CLI:

1. Clone repository (replace `<repo-url>` with the repository remote)
   ```
   git clone <repo-url>
   ```

2. Change into the app directory
   ```
   cd test-app/test-app
   ```

3. Install dependencies (optional — no external deps are declared)
   ```
   npm install
   ```

4. Start the quiz
   ```
   npm start
   ```
   or
   ```
   node index.js
   ```

You can also run the file directly (make it executable first):
```
chmod +x index.js
./index.js
```

---

## Usage

When you run the app you will be prompted to:

- Select a category
- Choose how many questions to answer (e.g. all, or a smaller sample)
- Answer each question interactively (select a choice)
- See per-question feedback and a progress indicator
- View a final summary, score, and explanations for any incorrect answers

The UI runs in the terminal using a readline-based input helper.

---

## Data format / Configuration

Question data is stored in JSON under `data/questions.json`. Questions are organized by category. A typical structure looks like:

- Root object: category keys mapping to arrays of question objects
- Each question object commonly includes:
  - `id` — a unique identifier (string or number)
  - `question` — the question text
  - `choices` — an array of choice strings
  - `answer` — the correct choice (commonly stored as an index referencing `choices`)
  - `explanation` — optional explanation shown for incorrect answers

Example (illustrative):
```json
{
  "JavaScript": [
    {
      "id": "js-01",
      "question": "What does `let` do?",
      "choices": ["Declares a block-scoped variable", "Declares a global variable"],
      "answer": 0,
      "explanation": "`let` declares block-scoped variables in ES6+."
    }
  ]
}
```

Note: Keep the JSON valid and consistent with the existing file format. When adding or editing questions, follow the existing pattern in `data/questions.json`.

---

## Project structure

Top-level layout (app folder is `test-app/test-app`):

- index.js — CLI entry point (shebang, main executable)
- package.json — project metadata and scripts (ES module: `"type": "module"`)
- data/
  - questions.json — question database (categories → question arrays)
- src/
  - input.js — readline-based input helpers (prompt, select, confirm)
  - quiz.js — Quiz class and game logic (shuffle, score, reporting)
  - colors.js — ANSI color helpers
- .DS_Store, __MACOSX, etc. — macOS artifacts (see housekeeping below)

---

## NPM scripts

Defined in `package.json`:

- start — start the CLI
  ```
  npm start
  ```
  runs: `node index.js`

- test — placeholder
  ```
  npm test
  ```
  runs: `node --test` (no tests included in the repo by default)

---

## Contributing

Contributions are welcome. Suggested workflow:

1. Fork the repo and create a feature branch.
2. Add or edit questions under `data/questions.json` following the existing schema/pattern.
3. Run the app locally to verify behavior:
   ```
   cd test-app/test-app
   node index.js
   ```
4. Open a pull request with a clear description of changes.

Notes:
- The codebase uses ES modules (`import`/`export`) — keep the style consistent.
- No external dependencies are currently used. If you add one, update `package.json`.
- Add tests if you introduce logic that benefits from automated verification.

---

## License

The project license is declared as MIT in `package.json`. If you intend to reuse or publish, consider adding an explicit LICENSE file to the repository root for clarity.

---

## Housekeeping

Please remove platform-specific and generated artifacts before committing:

- Remove macOS metadata directories/files such as `__MACOSX/` and `.DS_Store`.
- Add a `.gitignore` entry to ignore these and other unwanted artifacts:
  ```
  .DS_Store
  __MACOSX/
  node_modules/
  ```
Keeping the repo clean improves cross-platform collaboration.

---

If you want, I can also:
- Draft a LICENSE file (MIT text),
- Produce a sample .gitignore,
- Add a minimal GitHub Actions workflow to run tests/lint on push.
