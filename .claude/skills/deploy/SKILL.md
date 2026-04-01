---
name: deploy
description: Run tests, build the production bundle, and push to staging
---

Deploy the application to the staging environment by following these steps in order:

## Step 1: Run Tests

Run the project's test suite first. If tests fail, stop immediately and report the failures — do not proceed to build or deploy.

```bash
npm test
```

If there are no tests configured (e.g., no test script or test files), note this and continue to the next step.

## Step 2: Build Production Bundle

Run the production build. If the build fails, stop and report the error — do not proceed to deploy.

```bash
npm run build
```

Confirm the `dist/` directory was created and is non-empty.

## Step 3: Push to Staging

Deploy the contents of `dist/` to the staging environment. Use whatever deployment mechanism is configured for this project (e.g., `npm run deploy:staging`, a CLI tool, or an upload command). If no staging deployment command is configured, report what was built and ask the user how they'd like to push to staging.

## After Each Step

- Report success or failure clearly.
- On any failure, show the relevant error output and stop — do not proceed to the next step.
- On full success, summarize: tests passed (or skipped), build succeeded, and staging deploy completed.
