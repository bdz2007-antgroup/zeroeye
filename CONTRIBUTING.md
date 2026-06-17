# Contributing to ZeroEye

Thank you for your interest in contributing to ZeroEye! This guide will help you get started with the development environment, build process, and pull request workflow.

## Getting Started

### Prerequisites

Before you begin, ensure you have the following installed:

- **Python**: 3.8 or later
- **Git**: Latest version
- **Build tools**: `make`, `gcc` (for C modules)
- **Rust**: 1.70+ (for backend components)
- **Node.js**: 18+ (for frontend tooling)

### Clone the Repository

```bash
git clone https://github.com/lobster-trap/zeroeye.git
cd zeroeye
```

### Install Dependencies

```bash
# Python dependencies
pip install -r requirements.txt

# Rust dependencies (if applicable)
cargo fetch

# Node dependencies (if applicable)
npm install
```

## Building the Project

Run the build script to compile all modules and generate diagnostic artifacts:

```bash
python3 build.py
```

The build process will:
1. Compile all source modules
2. Run tests and validation checks
3. Generate encrypted diagnostic logs in `diagnostic/build-XXX.logd`
4. Create metadata files in `diagnostic/build-XXX.json`

**Important**: The diagnostic artifacts are required for all pull requests and must be included in your submission.

## Pull Request Workflow

### 1. Fork and Branch

```bash
# Fork the repository on GitHub, then:
git remote add upstream https://github.com/lobster-trap/zeroeye.git
git checkout -b feature/your-feature-name
```

### 2. Make Changes

- Follow the code style guidelines (see `.editorconfig`)
- Write clear commit messages
- Add tests for new functionality
- Update documentation as needed

### 3. Test Locally

```bash
# Run the full build
python3 build.py

# Verify diagnostic artifacts were generated
ls -la diagnostic/
```

### 4. Commit and Push

```bash
git add .
git commit -m "feat: add your feature description"
git push origin feature/your-feature-name
```

### 5. Create Pull Request

- Use the PR template at `.github/pull_request_template.md`
- Include the generated diagnostic artifacts (`diagnostic/build-XXX.logd` and `diagnostic/build-XXX.json`)
- Reference any related issues (e.g., `Closes #123`)
- Provide a clear description of changes and testing performed

## Code Style

This project uses `.editorconfig` to enforce consistent formatting across editors. Key rules:

- **Python/Rust/C++**: 4 spaces indentation
- **TypeScript/JavaScript**: 2 spaces indentation
- **Makefile**: Tabs
- **YAML/JSON/Markdown**: 2 spaces indentation

Ensure your editor respects the `.editorconfig` settings.

## Diagnostic Artifacts

Every build generates encrypted diagnostic logs that help maintainers verify your changes:

- **`diagnostic/build-XXX.logd`**: Encrypted build log (required in PR)
- **`diagnostic/build-XXX.json`**: Metadata including decryption credentials

These files must be committed with your pull request. The maintainer will use them to verify your build environment and test results.

## Questions?

If you have questions or need help, please:
1. Check existing issues and discussions
2. Open a new issue with the `question` label
3. Reference relevant documentation

Thank you for contributing to ZeroEye!
