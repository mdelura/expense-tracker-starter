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

Single-page React app (Vite + React 19) with no routing, no state management library, and no backend.

**Component tree:**
```
App
├── Summary          — computes and displays income/expenses/balance from transactions
├── TransactionForm  — owns form field state; calls onAdd(transaction) on submit
└── TransactionList  — owns filter state; renders filtered transactions table
```

**State ownership:**
- `App` holds the `transactions` array (single source of truth) and passes it down
- `TransactionForm` owns its own local form field state (description, amount, type, category)
- `TransactionList` owns its own local filter state (filterType, filterCategory)

**Data shape:**
```js
{ id: number, description: string, amount: number, type: "income"|"expense", category: string, date: "YYYY-MM-DD" }
```

**Categories:** food, housing, utilities, transport, entertainment, salary, other — duplicated in `TransactionForm` and `TransactionList` (no shared constants file yet).

**Known intentional issues (part of a course):**
- Transaction item 4 ("Freelance Work") is miscategorized as `type: "expense"` despite being income
- The UI is intentionally minimal/unstyled beyond basic CSS in `src/App.css`
- A `.delete-btn` CSS class exists in `App.css` but the delete button is not yet implemented
