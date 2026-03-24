# Contributing to LearnVault

Welcome to LearnVault! We're excited that you're interested in contributing to our project. LearnVault is a decentralized learning platform built on the Stellar blockchain with Soroban smart contracts, featuring a modern React 19 frontend. Whether you're a seasoned blockchain developer, a frontend enthusiast, a documentation writer, or someone just starting their open-source journey, we welcome contributors of all skill levels and backgrounds.

This guide will help you understand how you can contribute to LearnVault and get started with the development process.

## Ways to Contribute

There are many ways you can contribute to LearnVault, and we value all types of contributions:

### 1. Frontend Code
Help us build and improve the user interface using React 19, TypeScript, and Vite. Whether it's implementing new features, fixing bugs, or improving the user experience, your frontend skills are valuable here.

### 2. Smart Contract Code
Contribute to our Soroban smart contracts written in Rust. We have six contracts in the `/contracts` directory that power the core functionality of LearnVault's decentralized learning platform.

### 3. Documentation
Improve our documentation, write tutorials, create examples, or help clarify existing content. Good documentation makes the project accessible to everyone.

### 4. Bug Reports
Found a bug? Report it! Detailed bug reports with reproduction steps help us improve the quality and reliability of LearnVault.

### 5. Community Support
Help other contributors by answering questions, reviewing pull requests, or participating in discussions. Building a supportive community is just as important as writing code.

## Local Setup

Follow these steps to set up LearnVault on your local machine. By the end of this process, you'll have a fully functional development environment.

### Step 1: Clone the Repository

First, clone the LearnVault repository to your local machine:

```bash
git clone https://github.com/bakeronchain/learnvault.git
cd learnvault
```

### Step 2: Install Dependencies

Install the Node.js dependencies using npm:

```bash
npm install
```

Make sure you have [Node.js](https://nodejs.org/) installed on your system. We recommend using the latest LTS version.

### Step 3: Install Rust and Soroban CLI

LearnVault's smart contracts are written in Rust and deployed using the Soroban CLI. You'll need both installed to work with the contracts.

**Install Rust:**
Follow the official installation guide at [https://www.rust-lang.org/tools/install](https://www.rust-lang.org/tools/install)

**Install Soroban CLI:**
Follow the Soroban setup guide at [https://soroban.stellar.org/docs/getting-started/setup](https://soroban.stellar.org/docs/getting-started/setup)

### Step 4: Start the Development Server

Once all dependencies are installed, start the frontend development server:

```bash
npm start
```

The application should now be running locally, typically at `http://localhost:5173` (Vite's default port).

### Step 5: Configure Freighter Wallet for Stellar Testnet

To interact with the Stellar blockchain and test smart contract functionality, you'll need the Freighter wallet extension configured for the testnet:

1. Install the Freighter browser extension from [https://www.freighter.app/](https://www.freighter.app/)
2. Create a new wallet or import an existing one
3. Switch the network to **Testnet** in the Freighter settings
4. Fund your testnet account using the [Stellar Testnet Friendbot](https://laboratory.stellar.org/#account-creator?network=test)

You're now ready to start contributing to LearnVault!

## Branching and Pull Requests

To keep our codebase organized and make the review process smooth, we follow specific conventions for branching and pull requests.

### Branch Naming Convention

When creating a new branch for your contribution, use one of the following prefixes based on the type of change:

- **`feat/`** - For new features or enhancements
  - Example: `feat/add-course-rating-system`
- **`fix/`** - For bug fixes
  - Example: `fix/wallet-connection-timeout`
- **`docs/`** - For documentation changes
  - Example: `docs/update-api-examples`

### Pull Request Description Template

When you open a pull request, please include the following information in your PR description:

1. **Summary of Changes**: A clear description of what you changed and why. Explain the problem you're solving or the feature you're adding.

2. **Related Issue Reference**: Link to the GitHub issue that your PR addresses. Use keywords like "Closes #123" or "Fixes #456" to automatically close the issue when the PR is merged.

3. **Testing Steps**: Describe how you tested your changes. Include specific steps that reviewers can follow to verify your work. For example:
   - Steps to reproduce the bug (for fixes)
   - How to test the new feature (for features)
   - Which test files were added or modified

### Review and Merge Process

Before your pull request can be merged, it must meet the following requirements:

1. **Link PR to GitHub Issue**: Make sure your PR is linked to the relevant GitHub issue. This helps us track which issues are being worked on and provides context for reviewers.

2. **CI Checks Must Pass**: All automated checks must pass before your PR can be merged. This includes:
   - GitHub Actions workflows for smart contracts
   - GitHub Actions workflows for frontend code
   - Any linting or formatting checks

3. **Maintainer Approval**: At least one project maintainer must review and approve your PR before it can be merged. Reviewers may request changes or ask questions to ensure code quality and consistency.

Once all checks pass and you have the required approval, a maintainer will merge your PR. Thank you for your contribution!

## Code Standards

To maintain consistency and quality across the LearnVault codebase, we follow specific coding standards for both frontend and smart contract development.

### Frontend

All frontend code in LearnVault must adhere to the following standards:

#### TypeScript Only

All frontend code must be written in **TypeScript**. We do not accept JavaScript files in the codebase. TypeScript provides type safety, better tooling, and helps catch errors early in the development process.

#### No `any` Type

The use of the `any` type is **prohibited** in our TypeScript code. Using `any` defeats the purpose of TypeScript's type system and can lead to runtime errors. Instead:

- Use specific types or interfaces
- Use `unknown` if the type is truly unknown, and narrow it with type guards
- Use generics when appropriate
- If you're unsure about the correct type, ask for help in your PR or issue discussion

#### Use @stellar/design-system Components

When building UI components, you must use components from the **`@stellar/design-system`** library instead of creating custom equivalents. This ensures:

- Visual consistency across the application
- Accessibility compliance
- Reduced maintenance burden
- Alignment with Stellar ecosystem standards

If you need a component that doesn't exist in the design system, discuss it with the maintainers before implementing a custom solution.

#### Follow Project Linting Configuration

LearnVault uses ESLint and Prettier to enforce code style and quality. The project's existing configuration is the authoritative style guide. Before submitting your PR:

- Run `npm run lint` to check for linting errors
- Run `npm run format` (if available) or configure your editor to format on save
- Fix any linting errors or warnings
- Do not modify the ESLint or Prettier configuration without discussing it with maintainers first

Your code must pass all linting checks in CI before it can be merged.

### Smart Contracts

All smart contract code in LearnVault must adhere to the following standards to ensure quality, security, and maintainability.

#### Format with `cargo fmt`

All Rust contract code must be formatted with **`cargo fmt`** before submission. Consistent formatting makes code reviews easier and maintains a uniform codebase. Before submitting your PR:

- Run `cargo fmt` in the `/contracts` directory or in the specific contract directory you're working on
- Ensure your editor is configured to format Rust code on save (optional but recommended)
- All formatting checks must pass in CI

#### Unit Tests Required

Every pull request that touches a Soroban contract **must include unit tests** for the changed logic. Testing is critical for smart contracts because:

- Contract bugs can have serious consequences in a blockchain environment
- Tests serve as documentation for how the contract should behave
- Tests prevent regressions when making future changes

Your tests should:

- Cover the main functionality of your changes
- Test edge cases and error conditions
- Use descriptive test names that explain what is being tested
- Be located in the same file as the contract code (following Rust conventions with `#[cfg(test)]` modules)

#### Contract Scope

LearnVault has **six smart contracts** located in the `/contracts` directory. When contributing to smart contracts, familiarize yourself with the existing contract structure and follow the patterns established in the codebase.

If you're proposing a new contract or significant changes to contract architecture, please open an issue for discussion before starting implementation.

#### Follow Soroban Best Practices

Follow the official Soroban best practices and conventions as documented in the [Soroban documentation](https://soroban.stellar.org/docs). This includes:

- Proper error handling using Soroban's error types
- Efficient storage patterns
- Gas optimization considerations
- Security best practices for smart contract development

## Finding Issues to Work On

We use GitHub issue labels to help contributors find tasks that match their interests and skill level. Here's what each label means:

### `good first issue`

Issues labeled with **`good first issue`** are specifically curated for newcomers to the project. These issues are:

- Well-scoped and clearly defined
- Typically smaller in scope and complexity
- Great for learning the codebase and contribution workflow
- Often include additional context or guidance to help you get started

**If you're new to LearnVault or open-source contribution in general, we recommend starting with a `good first issue`.** These tasks are designed to give you a positive first experience and help you become familiar with our development process.

### `smart contract`

Issues labeled with **`smart contract`** involve work on our Rust-based Soroban smart contracts. These issues might include:

- Implementing new contract functionality
- Fixing bugs in existing contracts
- Optimizing contract performance or gas usage
- Adding or improving contract tests
- Updating contract documentation

If you're interested in blockchain development, Rust programming, or Soroban smart contracts, look for issues with this label.

### `frontend`

Issues labeled with **`frontend`** involve work on our React 19 and TypeScript user interface. These issues might include:

- Building new UI components or features
- Fixing frontend bugs or improving user experience
- Implementing responsive design improvements
- Integrating with the Stellar design system
- Adding or improving frontend tests

If you enjoy working with React, TypeScript, or UI/UX development, look for issues with this label.

### How to Find Issues

To browse issues by label, visit our [GitHub Issues page](https://github.com/bakeronchain/learnvault/issues) and use the label filters. You can also combine labels to narrow your search (for example, `good first issue` + `frontend` to find beginner-friendly frontend tasks).

Don't see an issue that interests you? Feel free to propose new features or improvements by opening a new issue for discussion!

## Code of Conduct

LearnVault is committed to providing a welcoming, inclusive, and harassment-free experience for everyone. All contributors are expected to adhere to our Code of Conduct.

Please read our [Code of Conduct](CODE_OF_CONDUCT.md) before contributing. By participating in this project, you agree to abide by its terms and help us maintain a positive and respectful community.

If you experience or witness unacceptable behavior, please report it to the project maintainers. We take all reports seriously and will respond appropriately.

---

Thank you for contributing to LearnVault! Your efforts help make decentralized education accessible to everyone. 🚀
