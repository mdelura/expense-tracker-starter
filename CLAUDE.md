# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

```bash
npm install       # Install dependencies (required before first run)
npm run dev       # Start dev server at http://localhost:5173
npm run build     # Production build
npm run lint      # Run ESLint
npm run preview   # Preview production build
```

There are no tests in this project.

## Architecture

This is a single-page React app (Vite + React 19) with no routing, no state management library, and no backend. All state lives in a single `useState` hook in `src/App.jsx`.

**Known intentional issues (part of a course):**
- Bug: `amount` is stored as a string, so `reduce` concatenates instead of summing — totals are wrong
- Transaction item 4 ("Freelance Work") is miscategorized as `type: "expense"` despite being income
- The UI is intentionally minimal/unstyled beyond basic CSS in `src/App.css`
- A `.delete-btn` CSS class exists in `App.css` but the delete button is not yet implemented in JSX

**Data shape:**
```js
{ id: number, description: string, amount: string, type: "income"|"expense", category: string, date: "YYYY-MM-DD" }
```

**Categories:** food, housing, utilities, transport, entertainment, salary, other
