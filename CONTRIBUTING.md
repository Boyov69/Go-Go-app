# Contributing to Go-Go App

Thank you for considering contributing to the Go-Go App project! This document outlines the process for contributing to the project and the standards we expect from contributors.

## Code of Conduct

By participating in this project, you agree to abide by our Code of Conduct. Please read it before contributing.

## How Can I Contribute?

### Reporting Bugs

This section guides you through submitting a bug report. Following these guidelines helps maintainers understand your report, reproduce the behavior, and find related reports.

Before creating bug reports, please check the issue tracker as you might find that you don't need to create one. When you are creating a bug report, please include as many details as possible:

* **Use a clear and descriptive title** for the issue to identify the problem.
* **Describe the exact steps which reproduce the problem** in as many details as possible.
* **Provide specific examples to demonstrate the steps**. Include links to files or GitHub projects, or copy/pasteable snippets, which you use in those examples.
* **Describe the behavior you observed after following the steps** and point out what exactly is the problem with that behavior.
* **Explain which behavior you expected to see instead and why.**
* **Include screenshots and animated GIFs** which show you following the described steps and clearly demonstrate the problem.
* **If the problem is related to performance or memory**, include a CPU profile capture with your report.
* **If the problem wasn't triggered by a specific action**, describe what you were doing before the problem happened.

### Suggesting Enhancements

This section guides you through submitting an enhancement suggestion, including completely new features and minor improvements to existing functionality.

* **Use a clear and descriptive title** for the issue to identify the suggestion.
* **Provide a step-by-step description of the suggested enhancement** in as many details as possible.
* **Provide specific examples to demonstrate the steps**. Include copy/pasteable snippets which you use in those examples.
* **Describe the current behavior** and **explain which behavior you expected to see instead** and why.
* **Include screenshots and animated GIFs** which help you demonstrate the steps or point out the part of the application which the suggestion is related to.
* **Explain why this enhancement would be useful** to most users.
* **List some other applications where this enhancement exists.**

### Pull Requests

* Fill in the required template
* Do not include issue numbers in the PR title
* Include screenshots and animated GIFs in your pull request whenever possible
* Follow the style guides
* Document new code
* End all files with a newline
* Avoid platform-dependent code

## Style Guides

### Git Commit Messages

* Use the present tense ("Add feature" not "Added feature")
* Use the imperative mood ("Move cursor to..." not "Moves cursor to...")
* Limit the first line to 72 characters or less
* Reference issues and pull requests liberally after the first line
* Consider starting the commit message with an applicable emoji:
    * 🎨 `:art:` when improving the format/structure of the code
    * 🐎 `:racehorse:` when improving performance
    * 🚱 `:non-potable_water:` when plugging memory leaks
    * 📝 `:memo:` when writing docs
    * 🐛 `:bug:` when fixing a bug
    * 🔥 `:fire:` when removing code or files
    * 💚 `:green_heart:` when fixing the CI build
    * ✅ `:white_check_mark:` when adding tests
    * 🔒 `:lock:` when dealing with security
    * ⬆️ `:arrow_up:` when upgrading dependencies
    * ⬇️ `:arrow_down:` when downgrading dependencies
    * 👕 `:shirt:` when removing linter warnings

### JavaScript/TypeScript Style Guide

* Use 2 spaces for indentation
* Use semicolons
* Use single quotes for strings
* Prefer arrow functions
* Use template literals for string concatenation
* Use destructuring assignment
* Use the spread operator
* Use async/await over Promises
* Use ESLint with the provided configuration

### Flutter/Dart Style Guide

* Use 2 spaces for indentation
* Follow the official [Dart style guide](https://dart.dev/guides/language/effective-dart/style)
* Use named parameters for clarity
* Prefer const constructors when possible
* Use the flutter_lints package with the provided configuration

## Development Environment Setup

### Backend (Node.js)

1. Install Node.js (v18+) and npm
2. Clone the repository
3. Navigate to the backend directory: `cd backend`
4. Install dependencies: `npm install`
5. Set up environment variables (copy `.env.example` to `.env` and fill in the values)
6. Start the development server: `npm run dev`

### Frontend (Next.js)

1. Navigate to the frontend directory: `cd frontend`
2. Install dependencies: `npm install`
3. Set up environment variables (copy `.env.example` to `.env` and fill in the values)
4. Start the development server: `npm run dev`

### Mobile (Flutter)

1. Install Flutter SDK (follow the [official installation guide](https://flutter.dev/docs/get-started/install))
2. Navigate to the mobile directory: `cd mobile/go_go`
3. Install dependencies: `flutter pub get`
4. Run the app: `flutter run`

## Testing

### Backend Testing

```bash
cd backend
npm test
```

### Frontend Testing

```bash
cd frontend
npm test
```

### Mobile Testing

```bash
cd mobile/go_go
flutter test
```

## Continuous Integration

We use GitHub Actions for continuous integration. Every pull request will be automatically tested, and the results will be displayed in the pull request.

## Deployment

Deployment is handled automatically when changes are merged into the main branch. The deployment process is documented in the main README.md file.

## Questions?

If you have any questions about contributing, please open an issue or contact the project maintainers.

Thank you for contributing to the Go-Go App project!
