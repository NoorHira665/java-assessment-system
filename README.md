# Survey & Test Application

A Java console application for creating, taking, and grading surveys and tests. Supports multiple question types, persistent serialized storage, and automatic test grading.

## Features

- **Surveys** — create, take, save, load, modify, and tabulate survey responses
- **Tests** — everything surveys support, plus correct answers, grading, and optional answer display
- **6 question types** — True/False, Multiple Choice, Short Answer, Essay, Date, and Matching
- **Persistent storage** — surveys, tests, and responses are serialized to disk and reloaded across sessions
- **Auto-grading** — tests are graded automatically, with essay questions flagged as non-auto-gradable
- **Response tabulation** — frequency breakdowns for all gradable question types

## How to Run

Compile and run from the project root:

```bash
javac *.java
java Main
```

No external dependencies — uses the Java standard library only.

## Project Structure

| File | Description |
|------|-------------|
| `Main.java` | Entry point — top-level menu for Survey and Test modes |
| `Survey.java` | Core survey logic: create, display, take, save, load, modify, tabulate |
| `Test.java` | Extends Survey with correct answers, display with/without answers, and grading |
| `Question.java` | Abstract base class for all question types |
| `TrueFalse.java` | True/False question |
| `MultipleChoice.java` | Multiple choice question with configurable choices |
| `ShortAnswer.java` | Short answer question (200-character limit) |
| `Essay.java` | Open-ended essay question |
| `Date.java` | Date question with MM/DD/YYYY format validation |
| `Matching.java` | Matching question with two-column left/right pairing |
| `ResponseCorrectAnswer.java` | Stores and serializes responses and correct answers |
| `SerializationHelper.java` | Generic serialization and deserialization utility |
| `FileUtils.java` | File I/O utilities |
| `Validation.java` | Input validation helpers |
| `Input.java` | User input utilities |
| `FSConfig.java` | File system path configuration |
| `TimeHelper.java` | Timestamp-based file name generation |
| `Output.java` | Console output utility |

## Question Types

| Type | Validation | Auto-gradable |
|------|-----------|---------------|
| True/False | T or F only | Yes |
| Multiple Choice | Valid choice number | Yes |
| Short Answer | Under 200 characters | Yes |
| Essay | Any input accepted | No |
| Date | MM/DD/YYYY format | Yes |
| Matching | NumChar format (e.g. 1C) | Yes |

## Storage

Surveys, tests, and responses are serialized to the following directories:

```
serialSave/
├── Survey/
├── Test/
└── Response/
```
