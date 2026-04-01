---
name: Project Architecture and Known Issues
description: Key architectural decisions, intentional course issues, and patterns observed in first full review
type: project
---

Single-page React 19 + Vite app. No routing, no state management library, no backend, no tests.

Component tree: App -> Summary, TransactionForm, TransactionList. App holds transactions array as single source of truth.

**Known intentional course issues (do not flag as new bugs):**
- Transaction id:4 "Freelance Work" has type:"expense" but should be "income" — this is a deliberate teaching exercise
- No shared constants file for categories array (duplicated in TransactionForm and TransactionList) — acknowledged, not yet addressed
- CSS is intentionally styled (not minimal — it has custom properties, animations, fonts); CLAUDE.md description of "minimal" is outdated

**Decisions confirmed in code:**
- `id` generation uses `Date.now()` — collision-prone but acceptable for a no-backend demo
- `handleAdd` uses spread (`[...transactions, transaction]`) instead of functional updater — minor correctness gap under React StrictMode
- `window.confirm` used for delete confirmation in TransactionList line 54 — inline, long handler
- No `useMemo` anywhere in the codebase
- StrictMode is enabled in main.jsx

**Why:** Course project; simplicity is intentional. **How to apply:** Flag real bugs and maintainability gaps; do not penalize deliberate simplifications unless they would cause actual problems for a learner.
