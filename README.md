# Playwright Automation Framework

Modern End-to-End UI + API Automation Framework using Playwright with JavaScript (ESM), Page Object Model (POM), Parallel Execution, and Allure Reporting.

---

# Tech Stack

- Playwright
- JavaScript (ESM Modules)
- Node.js
- Allure Reports
- Page Object Model (POM)

---

# Project Structure

```Terminal
playwright-framework/
│
├── pages/
│   ├── LoginPage.js
│   ├── InventoryPage.js
│   └── CheckoutPage.js
│
├── tests/
│   ├── login.spec.js
│   ├── order.spec.js
│   └── api.spec.js
│
├── utils/
│   └── testData.js
│
├── playwright.config.js
├── package.json
└── README.md
```

---

# Features

- Modern Playwright Framework
- ES Modules Support
- Page Object Model Design Pattern
- Cross Browser Testing
- Parallel Execution
- API Testing
- Screenshot on Failure
- Video Recording on Failure
- Trace Collection
- Allure Reporting

---

# Installation

## Clone Repository

```Terminal
git clone https://github.com/venkateswaran2248-gif/Ejada_Assignments.git
```

## Navigate to Project

```Terminal
cd Ejada_Assignments
```

## Install Dependencies

```Terminal
npm install
```

## Install Playwright Browsers

```Terminal
npx playwright install
```

---

# Package.json

```json
{
  "name": "playwright-framework",
  "version": "1.0.0",
  "type": "module",
  "scripts": {
    "test": "playwright test",
    "allure": "allure open"
  },
  "devDependencies": {
    "@playwright/test": "^1.45.0",
    "allure-playwright": "^2.0.0"
  }
}
```

---

# Playwright Configuration

```js
// playwright.config.js
import { defineConfig, devices } from '@playwright/test';

export default defineConfig({
  testDir: './tests',

  fullyParallel: true,

  retries: 1,

  reporter: [
    ['html'],
    ['allure-playwright']
  ],

  use: {
    baseURL: 'https://www.saucedemo.com',
    trace: 'on-first-retry',
    screenshot: 'only-on-failure',
    video: 'retain-on-failure'
  },

  projects: [
    {
      name: 'chromium',
      use: { ...devices['Desktop Chrome'] }
    },
    {
      name: 'firefox',
      use: { ...devices['Desktop Firefox'] }
    }
  ]
});
```

---

# Test Data

```js
// utils/testData.js
export const users = {
  valid: {
    username: 'standard_user',
    password: 'secret_sauce'
  },
  invalid: {
    username: 'invalid_user',
    password: 'wrong'
  },
  locked: {
    username: 'locked_out_user',
    password: 'secret_sauce'
  }
};
```

---

# Page Object Model

## LoginPage.js

```js
export class LoginPage {
  constructor(page) {
    this.page = page;
    this.username = page.locator('#user-name');
    this.password = page.locator('#password');
    this.loginBtn = page.locator('#login-button');
    this.error = page.locator('[data-test="error"]');
  }

  async goto() {
    await this.page.goto('/');
  }

  async login(username, password) {
    await this.username.fill(username);
    await this.password.fill(password);
    await this.loginBtn.click();
  }
}
```

---

# UI Test Cases

## Login Test

- Valid Login
- Invalid Login
- Locked User Login

## Order Flow Test

- Login
- Add Product to Cart
- Checkout
- Verify Order Success

---

# API Testing

## API Scenarios

- Generate Token
- Get Books
- Create Order

## API Base URL

```Terminal
https://simple-books-api.glitch.me
```

---

# Run Tests

## Execute All Tests

```Terminal
npx playwright test
```

## Parallel Execution

```Terminal
npx playwright test --workers=4
```

## Run Specific Test File

```Terminal
npx playwright test tests/login.spec.js
```

## Run on Chromium

```Terminal
npx playwright test --project=chromium
```

## Run on Firefox

```Terminal
npx playwright test --project=firefox
```

---

# Allure Report Setup

## Install Allure

```Terminal
npm install -D allure-playwright
```

## Generate Report

```Terminal
npx allure generate ./allure-results --clean
```

## Open Report

```Terminal
npx allure open
```

---

# Reports

- HTML Report
- Allure Report
- Screenshots on Failure
- Video Recording
- Trace Viewer

---

# Best Practices Used

- Page Object Model (POM)
- Reusable Methods
- Centralized Test Data
- Cross Browser Support
- Parallel Execution
- Clean Folder Structure

---

# Author

Venkateswaran

GitHub Repository:
https://github.com/venkateswaran2248-gif/Ejada_Assignments
