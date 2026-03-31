# Node.js Ecosystem Rules

When BootstrApp is scaffolding or injecting dependencies into a Node.js, JavaScript, or TypeScript project, adhere to the following rules:

## 1. Package Managers
- **Default Check**: Always default to `npm` unless the user specifically requests `pnpm`, `yarn`, or `bun`.
- **Consistency**: Never mix package managers (e.g., don't run `yarn install` if a `package-lock.json` already exists).

## 2. Dependency Injection
- **Install Commands**: Use `npm install <package>` for standard dependencies and `npm install -D <package>` for dev dependencies (like Tailwind, ESLint, TypeScript types).
- **TypeScript**: If the project is identified as TypeScript (e.g., has a `tsconfig.json`), ALWAYS install the corresponding `@types/` packages as dev dependencies.

## 3. Configuration Best Practices
- **ESModules over CommonJS**: Favor `"type": "module"` and `import/export` syntax in new setups.
- **Environment Variables**: Always append `.env` to the `.gitignore` immediately if you are adding database or auth packages. Generate a `.env.example` placeholder.

## 4. Default Tooling Choices
If the user asks for generic functionality, recommend these modern defaults:
- **Styling**: Tailwind CSS
- **Testing**: Vitest (over Jest, especially for Vite projects)
- **Fetching**: TanStack Query (React Query) or native fetch.

## 5. Scripting & Code Generation
- **PowerShell Expansion**: When writing raw code lines to files using PowerShell's `Out-File`, NEVER use single quotes (`'...'`) if the string contains escape characters like newlines (`` `n ``). Single quotes treat everything as raw literal strings. ALWAYS use double quotes (`"..."`) when echoing or outputting multi-line boilerplate so PowerShell correctly expands the breaks.