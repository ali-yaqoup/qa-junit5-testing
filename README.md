# Quality Assurance â€” JUnit 5 Testing Project

A Java homework assignment from the Software Quality Assurance course at An-Najah National University. The project exercises JUnit 5 testing techniques against a small set of business-logic classes: a calculator, a product model, a recipe/recipe-book domain, and a user-service stub.

## What's Implemented

### Source classes (`src/main/najah/code/`)

| Class | Description |
|---|---|
| `Calculator` | Arithmetic methods: varargs `add`, integer `divide`, recursive `factorial` |
| `Product` | Product entity with name, price, and quantity fields |
| `Recipe` | Recipe entity with ingredient list and price calculation |
| `RecipeBook` | Fixed-capacity collection of `Recipe` objects |
| `RecipeException` | Custom checked exception for invalid recipe operations |
| `UserService` | Stub authentication service (single hardcoded credential) |

### Test classes (`src/main/najah/test/`)

| Test class | Class under test | JUnit 5 techniques used |
|---|---|---|
| `CalculatorTest` | `Calculator` | `@ParameterizedTest` / `@CsvSource` for factorial, `assertAll`, `assertThrows`, `@Disabled`, `@Order`, `@BeforeAll` / `@AfterAll` lifecycle hooks |
| `ProductTest` | `Product` | Multiple assertions, boundary checks on price and quantity |
| `RecipeTest` | `Recipe` | Lifecycle hooks (`@BeforeEach`), exception handling, ingredient validation |
| `RecipeBookTest` | `RecipeBook` | Capacity boundary tests, add/delete/replace scenarios |
| `UserServiceSimpleTest` | `UserService` | Login success/failure, timeout assertions (`@Timeout`) |
| `Test_Suit` | All of the above | JUnit Platform `@Suite` grouping all test classes |

## Tech Stack

| Component | Detail |
|---|---|
| Language | Java (JDK 17+) |
| Test framework | JUnit 5 (Jupiter) |
| Build | Plain `javac` + JUnit Platform Console Standalone JAR |
| IDE used | IntelliJ IDEA |

## Project Structure

```
Quality-Assurance/
â””â”€â”€ Junit5-HW-50D4/
    â”œâ”€â”€ src/
    â”‚   â””â”€â”€ main/
    â”‚       â””â”€â”€ najah/
    â”‚           â”œâ”€â”€ code/        # Business-logic source classes
    â”‚           â””â”€â”€ test/        # JUnit 5 test classes
    â””â”€â”€ bin/                     # Compiled .class files (committed)
```

> Note: compiled `.class` files are committed under `bin/`. A `.gitignore` excluding build output would be a clean-up worth doing.

## Build & Run

```bash
cd Junit5-HW-50D4

# Compile
javac -d bin \
  src/main/najah/code/*.java \
  src/main/najah/test/*.java

# Run all tests (requires junit-platform-console-standalone jar on the classpath)
java -jar junit-platform-console-standalone.jar \
  --class-path bin \
  --scan-class-path
```

## Testing

The project explores five main JUnit 5 testing patterns:

1. **Parameterized tests** â€” `CalculatorTest` feeds six factorial cases via `@CsvSource`, verifying correct output for `n = 0..7`.
2. **Grouped assertions** â€” `assertAll` blocks in `CalculatorTest` ensure all sub-assertions are reported, not just the first failure.
3. **Exception testing** â€” `assertThrows` checks that `divide(x, 0)` throws `ArithmeticException` and that `factorial(-1)` throws `IllegalArgumentException`.
4. **Lifecycle hooks** â€” `@BeforeAll`, `@AfterAll`, `@BeforeEach`, and `@AfterEach` are present in every test class.
5. **Test suite** â€” `Test_Suit.java` registers all four test classes under a single `@Suite` entry point.

---

*Software Engineering degree, An-Najah National University*

## License & copyright

Copyright © 2026 Ali Yaqoub. All rights reserved.

This software and its contents are proprietary. Unauthorized copying, distribution, modification, or commercial use is prohibited without prior written permission from the copyright holder.
