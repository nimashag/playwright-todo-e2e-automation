# Playwright MiniProject: End-to-End Automation with the To-do App

This repository contains a small Playwright end-to-end automation project for the TodoMVC React demo app.

The main goal of the project is to practice browser automation with Playwright by:

- opening the to-do application
- adding new tasks
- marking tasks as completed
- filtering tasks by status
- clearing completed items
- generating traces, screenshots, videos, and HTML reports for debugging

## Project Structure

- `tests/todo-demo1.spec.js` - main end-to-end sanity test for the to-do app
- `tests/example.spec.js` - sample Playwright starter tests
- `playwright.config.js` - Playwright configuration
- `playwright-report/` - HTML test report output
- `test-results/` - failed test artifacts such as screenshots, videos, and traces

## Prerequisites

Before running the project, make sure you have:

- [Node.js](https://nodejs.org/) installed
- `npm` available in your terminal
- a supported browser environment

This project was built with:

- Playwright Test `^1.62.0`
- Node type definitions `^26.1.1`

## Installation

Install the project dependencies with:

```bash
npm install
```

If you are setting up Playwright browsers for the first time, run:

```bash
npx playwright install
```

If you want to install only the browser binaries used by this project, Playwright will automatically download them during `install`, but the command above is the simplest setup step.

## Running Tests

Run all Playwright tests:

```bash
npx playwright test
```

Run only the main to-do app sanity test:

```bash
npx playwright test tests/todo-demo1.spec.js
```

Run tests in headed mode so you can watch the browser:

```bash
npx playwright test --headed
```

Run the sanity test in headed mode on Chromium:

```bash
npx playwright test --headed --grep @sanity --project=chromium
```

Open the Playwright UI mode:

```bash
npx playwright test --ui
```

## Playwright Codegen

Playwright Codegen opens a browser and records your actions as Playwright code. This is useful when you want to quickly generate selectors and test steps for the to-do app.

Start Codegen against the TodoMVC React app:

```bash
npx playwright codegen https://todomvc.com/examples/react/dist/
```

Useful Codegen options:

- `--browser chromium|firefox|webkit` - choose which browser to record in
- `--viewport-size=1280,720` - set a custom viewport size
- `--output=tests/generated.spec.js` - save the generated script to a file
- `--target=javascript` - generate JavaScript output

Examples:

```bash
npx playwright codegen --browser chromium https://todomvc.com/examples/react/dist/
npx playwright codegen --output=tests/generated.spec.js https://todomvc.com/examples/react/dist/
```

While Codegen is open, you can:

- interact with the page normally
- inspect the generated steps in real time
- copy locators or assertions into your test file
- save the recorded script when you are done

## Reporting and Debugging

Generate and view the HTML report:

```bash
npx playwright show-report
```

This project is configured to keep useful debug artifacts when tests fail:

- screenshots on failure
- videos on failure
- traces on failure

You can open a saved trace with:

```bash
npx playwright show-trace
```

## Playwright Configuration

The project uses `playwright.config.js` with the following notable settings:

- tests are located in the `tests/` folder
- the default reporter is `html`
- tests run on `chromium`, `firefox`, and `webkit`
- traces are retained on failure
- screenshots are captured only on failure
- videos are retained on failure
- browser launch is slowed down slightly with `slowMo: 300` for easier observation

## Main Test Scenario

The primary test in `tests/todo-demo1.spec.js` performs the following steps against the TodoMVC React app:

1. opens `https://todomvc.com/examples/react/dist/`
2. adds multiple to-do items
3. marks selected items as completed
4. switches between `Active`, `Completed`, and `All` filters
5. verifies visible items and list contents
6. clears completed tasks

## Useful Notes

- The repository currently does not define custom `npm` scripts in `package.json`, so the recommended way to run Playwright is with `npx playwright ...`
- If you want to add scripts later, a common approach is to define `test`, `test:headed`, and `report` entries in `package.json`
- The test suite targets a public demo app, so internet access is required when the tests run

## Example Commands

```bash
npx playwright test
npx playwright test --headed
npx playwright test --ui
npx playwright show-report
```

## License

ISC
