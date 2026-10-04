# 🤖 WebdriverIO + TypeScript UI Automation

[![WebdriverIO Tests](https://github.com/archana-kannan/webdriverio-UI/actions/workflows/wdio.yml/badge.svg)](https://github.com/archana-kannan/webdriverio-UI/actions/workflows/wdio.yml)
![WebdriverIO](https://img.shields.io/badge/WebdriverIO%20v9-EA5906?logo=webdriverio&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?logo=typescript&logoColor=white)
![Mocha](https://img.shields.io/badge/Mocha-8D6748?logo=mocha&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-2088FF?logo=githubactions&logoColor=white)

A UI test automation framework using **WebdriverIO v9**, **TypeScript** and **Mocha**, structured around the **Page Object Model**. It tests the login flow of [the-internet.herokuapp.com](https://the-internet.herokuapp.com/login).

## ✨ Features

- **Page Object Model** with a shared base `Page` class and per-page objects
- **TypeScript** with strict compiler settings
- **Mocha BDD** (`describe` / `it`) with `expect-webdriverio` assertions
- **Headless Chrome on CI** (switches automatically when `CI=true`), visible browser locally
- **Spec reporter** for readable console output
- **GitHub Actions** pipeline on every push and pull request

## 📁 Project Structure

```
webdriverio-UI/
├── .github/workflows/wdio.yml        # CI pipeline
├── test/
│   ├── pageobjects/
│   │   ├── page.ts                   # base page: shared open() / navigation
│   │   ├── login.page.ts             # login page: selectors + login()
│   │   └── secure.page.ts            # secure area: flash message
│   └── specs/
│       └── test.e2e.ts               # login spec
├── wdio.conf.ts                      # runner, capabilities, framework, reporters
└── tsconfig.json
```

## 🧩 Page Object example

```ts
class LoginPage extends Page {
  public get inputUsername() { return $('#username'); }
  public get inputPassword() { return $('#password'); }
  public get btnSubmit()     { return $('button[type="submit"]'); }

  public async login(username: string, password: string) {
    await this.inputUsername.setValue(username);
    await this.inputPassword.setValue(password);
    await this.btnSubmit.click();
  }
}
```

## 🚀 Getting Started

**Prerequisites:** Node.js 18+, npm and Google Chrome. WebdriverIO downloads a matching ChromeDriver automatically.

```bash
git clone https://github.com/archana-kannan/webdriverio-UI.git
cd webdriverio-UI
npm ci
```

## ▶️ Running Tests

```bash
npm test                 # run all specs (Chrome visible locally)
CI=true npm test         # run headless, as on CI (macOS/Linux)
```

On Windows PowerShell, run headless with: `$env:CI="true"; npm test`

## 🔄 Continuous Integration

[`.github/workflows/wdio.yml`](.github/workflows/wdio.yml) runs on push and pull request to `main`, weekly, and on demand, using headless Chrome on Ubuntu.

## 🗺️ Roadmap

- [ ] Negative login scenarios (invalid credentials, validation messages)
- [ ] Cross-browser runs (Firefox, Edge)
- [ ] Allure reporting
- [ ] Cucumber/Gherkin feature files on top of the page objects

## 👩‍💻 Author

**Archana Kannan**, AI-Powered Software Quality Engineer
[GitHub](https://github.com/archana-kannan) · [LinkedIn](https://www.linkedin.com/in/archana-kannan-2021)
