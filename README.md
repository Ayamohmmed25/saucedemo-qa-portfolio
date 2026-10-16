# saucedemo-qa-portfolio
QA portfolio project for [SauceDemo](https://www.saucedemo.com), a public demo e-commerce site built for practicing test automation. The project combines **manual test documentation** with **automated UI tests** written in Java, Selenium WebDriver and TestNG.

## Project Goal

- Practice designing test cases the way QA teams do in real projects.
- Automate the most important user flows (login, inventory, purchase).
- Organize tests with TestNG: groups (smoke / regression), dependencies and suites.

## Tech Stack

| Tool | Purpose |
|---|---|
| Java | Programming language |
| Selenium WebDriver 4 | Browser automation |
| TestNG 7.9 | Test framework: annotations, assertions, groups, suites |
| Maven | Build and dependency management |
| Logback + SLF4J | Logging |
| IntelliJ IDEA | IDE |
| Git & GitHub | Version control |

## Project Structure

```
saucedemo-qa-portfolio/
├── src/test/java/tests/
│   └── LoginTests.java
├── src/test/resources/
├── docs/
│   └── test-cases.md
├── pom.xml
└── README.md
```

## Test Coverage

| Area | Scenarios | Group |
|---|---|---|
| Login | Valid login | smoke |
| Login | Wrong password shows an error | regression |
| Login | Locked-out user shows an error | regression |

## How to Run

**Requirements:** JDK 17 or higher, Maven, Google Chrome.

```bash
git clone https://github.com/Ayamohmmed25/saucedemo-qa-portfolio.git
cd saucedemo-qa-portfolio
mvn test
```

Or run `LoginTests` directly from IntelliJ (right-click, then Run).

## Test Results

> Add a screenshot of your TestNG run here, for example:
>
> `![Test results](screenshots/results.png)`

## Roadmap

- [x] Maven + Selenium + TestNG setup
- [x] Login tests with assertions
- [ ] Inventory tests
- [ ] End-to-end purchase flow using `dependsOnMethods`
- [ ] TestNG suites for smoke and regression (XML)
- [ ] Parallel execution
- [ ] Logging and HTML reports
- [ ] Manual test cases document (`docs/test-cases.md`)

## Author

**Aya Mohammed**
GitHub: [@Ayamohmmed25](https://github.com/Ayamohmmed25)
