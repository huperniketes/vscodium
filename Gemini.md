Write an instructional file for an AI assistant to perform code analysis, write tests, modify code, and build executables for the open-source VSCodium project at github.com/VSCodium/vscodium

# VSCodium AI Assistant Operational Instructions

## 1. Project Overview

*This document provides operational guidelines for an AI assistant working with the [VSCodium](https://github.com/VSCodium/vscodium) open-source project. VSCodium is a community-driven, freely-licensed binary distribution of Microsoft's VS Code editor, built from the VS Code source with telemetry and proprietary branding removed.*

---

## 2. Tech Stack

- **Framework:** Electron (for desktop app)
- **Language:** TypeScript, JavaScript
- **Build System:** Node.js, npm, yarn, shell scripts
- **Packaging:** Electron Builder, platform-specific scripts
- **Testing:** Mocha, Chai (unit/integration), custom scripts
- **CI/CD:** GitHub Actions, Azure Pipelines
- **Documentation:** Markdown, project wiki

### Build Dependencies
- **Node.js:** The build process requires Node.js version `22.14.0`.
- **macOS:** For macOS builds, a C++ compiler (`clang++`) is required, which is provided by Xcode. While the CI environment uses `macos-13`, the build scripts are compatible with macOS 11.7 and Xcode 13.2, provided the correct Node.js version is used.

---

## 3. Commands

- **Install Dependencies:**
    ```bash
    yarn install
    ```
- **Build VSCodium:**
    ```bash
    yarn run build
    ```
- **Run Tests:**
    ```bash
    yarn test
    ```
- **Package for Distribution:**
    ```bash
    yarn run package
    ```
- **Create Release Artifacts:**
    ```bash
    yarn run release
    ```
- **Lint Code:**
    ```bash
    yarn run lint
    ```

---

## 4. Coding Conventions & Style

- **Formatting:** Use Prettier and ESLint for code formatting and linting. Configuration is in `.prettierrc` and `.eslintrc`.
- **Naming Conventions:**
    - Files: kebab-case or camelCase (e.g., `main.js`, `build.js`)
    - Classes/Types: PascalCase (e.g., `BuildHelper`)
    - Variables/Functions: camelCase (e.g., `getBuildVersion`)
- **Architecture:** Follow the structure of the upstream VS Code project. VSCodium-specific scripts and patches are in the `build/` and `patches/` directories.
- **State Management:** Use standard JavaScript/TypeScript patterns; no external state management library is used.
- **Copyright:** All new files must include the standard VSCodium or upstream VS Code copyright.

---

## 5. Key File & Directory Locations

- **Build Scripts:** `build/`
- **Patches:** `patches/`
- **Source Code:** Mirrors VS Code's structure, e.g., `src/`, `product.json`, etc.
- **Release Scripts:** `build/azure-pipelines.yml`, `.github/workflows/`
- **Documentation:** `README.md`, `CONTRIBUTING.md`, `docs/`

---

## 6. Environment Variables

- **Build and packaging require environment variables for signing, publishing, and API keys.**
- See `.env.example` for a list of required variables.
- For local development, use a `.env` file (not committed to git).

---

## 7. AI Assistant Operational Guidelines

### 7.1 Code Analysis

- Analyze code for correctness, maintainability, and adherence to project conventions.
- When reviewing code, reference the upstream VS Code source for context.
- Highlight any deviation from open-source licensing or telemetry removal.

### 7.2 Writing Tests

- Place unit and integration tests alongside the code or in the `test/` directory.
- Use Mocha and Chai for test cases.
- Ensure tests cover VSCodium-specific changes and patches.

### 7.3 Modifying Code

- **Plan:** Before making changes, provide a summary of the purpose, affected files, and dependencies.
- **Context:** Explain how the change fits into the VSCodium architecture and its relationship to upstream VS Code.
- **Implementation:** Follow project conventions and ensure all modifications are open-source compliant.
- **Documentation:** Update relevant documentation if the change affects usage or build instructions.

### 7.4 Building Executables

- Use the provided build scripts (`yarn run build`, `yarn run package`, etc.).
- Ensure all platform-specific requirements are met (see `build/` scripts and documentation).
- Validate that the resulting binaries do not include telemetry or proprietary branding.

### 7.5 Commit & PR Guidelines

- Use [Conventional Commits](https://www.conventionalcommits.org/) for commit messages (e.g., `fix: remove telemetry from build script`).
- Reference related issues or upstream changes in commit messages and PR descriptions.
- Do not commit or push changes without explicit user approval.
- Always request confirmation before opening PRs or merging changes.

### 7.6 User Preferences

- **Validate Architecture:** Before making structural changes, describe the plan and request user confirmation.
- **Explanations:** Always provide a clear explanation and plan before executing changes.
- **Transparency:** Clearly state the purpose and impact of each action.

---

## 8. Additional Resources

- [VSCodium GitHub Repository](https://github.com/VSCodium/vscodium)
- [Upstream VS Code Source](https://github.com/microsoft/vscode)
- [VSCodium Documentation](https://github.com/VSCodium/vscodium/blob/master/README.md)
- [Contributing Guide](https://github.com/VSCodium/vscodium/blob/master/CONTRIBUTING.md)

----
