# Node.js Library Integration Notes

Consult these notes when a user requests specific libraries to avoid common configuration pitfalls and outdated practices.

## Tailwind CSS
- **Vite Projects**: Do NOT use PostCSS config (`postcss`, `autoprefixer`) or `npx tailwindcss init`. Tailwind v4 is the modern standard for Vite.
  - Setup: run `npm install tailwindcss @tailwindcss/vite`.
  - Config: Add `import tailwindcss from '@tailwindcss/vite'` to `vite.config.ts` and add `tailwindcss()` to the plugins array.
  - CSS: Create/Overwrite `src/index.css` with `@import "tailwindcss";`. ALWAYS use `Out-File -Encoding utf8` in PowerShell to avoid UTF-16 encoding errors that crash Vite builds.
- **Next.js Projects**: The `create-next-app` CLI handles Tailwind natively via the `--tailwind` flag. No manual configuration is needed.

## React Router
- Always use the modern Data Router syntax (`createBrowserRouter` / `RouterProvider`) instead of the old `<BrowserRouter>` component format when scaffolding from scratch.

## Prisma
- Always run `npx prisma init` after installation.
- Ensure you append `.env` to `.gitignore` immediately to prevent committing database credentials.
