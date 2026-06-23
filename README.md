# Finbro

Finbro is a Java command-line personal finance tracker for recording expenses, reviewing spending, and staying aware of monthly budget limits. It is built as a CS2113-style team project with Gradle, JUnit 5, Checkstyle, text UI tests, user documentation, and developer documentation.

## What Finbro does

- Records expenses with amount, category, and date.
- Supports both direct commands and guided walkthroughs for adding and deleting expenses.
- Displays all expenses or expenses in a category, with optional sorting and month filtering.
- Stores a monthly spending limit and warns when spending is close to or above the limit.
- Converts selected expenses between supported currencies using an offline rate table.
- Shows a text-based monthly spending visualization.
- Saves data locally to `./data/finbro.txt` between sessions.

## Quick start

### Prerequisites

- Java 17 or later
- Gradle wrapper included in this repository

### Run from source

On Windows:

```bash
.\gradlew.bat run
```

On macOS/Linux:

```bash
./gradlew run
```

### Build a runnable JAR

```bash
./gradlew shadowJar
```

The generated JAR is available under `build/libs/`. Run it with:

```bash
java -jar build/libs/Finbro.jar
```

## Basic commands

| Command | Example | Purpose |
| --- | --- | --- |
| `help` | `help add` | Show the command list or details for one command. |
| `add` | `add 12.50 food today` | Add an expense directly or start guided add mode. |
| `delete` | `delete food 1` | Delete an expense directly or start guided delete mode. |
| `view` | `view all -sort amount` | View expenses, with optional sorting and filtering. |
| `limit` | `limit 500` | Set or view the monthly spending limit. |
| `edit limit` | `edit limit` | Update the current limit interactively. |
| `currency` | `currency` | Convert an existing expense between supported currencies. |
| `visual` | `visual` | Show monthly spending as a text bar chart. |
| `exit` | `exit` | Save data and close Finbro. |

For full command syntax, examples, and troubleshooting, see the [User Guide](docs/UserGuide.md).

## Project structure

```text
src/main/java/seedu/finbro/    Application source code
src/test/java/seedu/finbro/    JUnit tests
docs/                          User guide, developer guide, and diagrams
text-ui-test/                  End-to-end text UI test assets
config/checkstyle/             Checkstyle rules
data/                          Local saved Finbro data
```

## Development

Run the automated test suite:

```bash
./gradlew test
```

Run Checkstyle:

```bash
./gradlew checkstyleMain checkstyleTest
```

Run the text UI test:

```bash
cd text-ui-test
./runtest.sh
```

On Windows, use `runtest.bat` instead.

## Documentation

- [User Guide](docs/UserGuide.md)
- [Developer Guide](docs/DeveloperGuide.md)
- [About Us](docs/AboutUs.md)

## Notes on saved data

Finbro writes user data to `./data/finbro.txt`. The first line stores the monthly limit, and each following line stores one expense. Avoid editing this file manually, as malformed values may cause Finbro to skip invalid entries when loading data.
