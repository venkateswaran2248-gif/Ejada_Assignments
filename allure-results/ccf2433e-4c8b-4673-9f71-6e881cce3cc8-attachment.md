# Instructions

- Following Playwright test failed.
- Explain why, be concise, respect Playwright best practices.
- Provide a snippet of code with the fix, if possible.

# Test info

- Name: example.spec.js >> get started link
- Location: tests\example.spec.js:13:5

# Error details

```
Error: page.goto: Target page, context or browser has been closed
Call log:
  - navigating to "https://playwright.dev/", waiting until "load"

```

# Test source

```ts
  1  | // @ts-check
  2  | import { test, expect } from '@playwright/test';
  3  | 
  4  | test('has title', async ({ page }) => {
  5  | 
  6  |   await page.goto('https://playwright.dev/');
  7  | 
  8  |   // Verify page title
  9  |   await expect(page).toHaveTitle(/Playwright/);
  10 | 
  11 | });
  12 | 
  13 | test('get started link', async ({ page }) => {
  14 | 
> 15 |   await page.goto('https://playwright.dev/');
     |              ^ Error: page.goto: Target page, context or browser has been closed
  16 | 
  17 |   // Click Get Started
  18 |   await page.getByRole('link', { name: 'Get started' }).click();
  19 | 
  20 |   // Verify URL
  21 |   await expect(page).toHaveURL(/.*intro/);
  22 | 
  23 |   // Verify heading exists
  24 |   await expect(
  25 |     page.getByRole('heading', { name: 'Installation' })
  26 |   ).toBeVisible();
  27 | 
  28 | });
```