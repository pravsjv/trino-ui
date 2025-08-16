# Agent Instructions for working with the Trino codebase

This document provides a set of instructions for an AI agent to follow when contributing to the Trino project. These instructions are based on the information found in the `README.md`, `.github/DEVELOPMENT.md`, and `.github/CONTRIBUTING.md` files.

## Core Principles

*   **Readability**: Code should be written to be easily understood by other developers. If a style rule conflicts with readability, prioritize readability.
*   **Consistency**: Maintain consistency with the surrounding code.
*   **Alphabetize**: When working with documentation, keep sections alphabetized.
*   **Avoid Abbreviations**: Do not use abbreviations, slang, or inside jokes. Well-known abbreviations like `max` and `min` are acceptable.

## Building and Testing

*   To build the project and install artifacts into your local Maven repository, run the following command. Note that this command skips the tests, which is recommended for local builds.
    ```bash
    ./mvnw clean install -DskipTests
    ```
*   Before submitting a pull request, run the following command to run Checkstyle and other validation checks:
    ```bash
    ./mvnw validate
    ```
*   To fix license headers, run:
    ```bash
    mvn license:format
    ```
*   To sort the `pom.xml` file, run:
    ```bash
    ./mvnw sortpom:sort
    ```

## Code Style

This project uses IntelliJ IDEA as the recommended IDE and follows the code style defined in the [airlift/codestyle](https://github.com/airlift/codestyle) repository.

Key code style guidelines include:

*   **Streams**: Use the Stream API where appropriate, but avoid it in performance-sensitive sections.
*   **Exceptions**: When throwing exceptions, categorize them. For example, `TrinoException` takes an error code.
*   **String Formatting**: Prefer `format()` for creating strings.
*   **Ternary Operator**: Avoid the ternary operator for all but the most trivial expressions.
*   **No Mocks**: Do not use mocking libraries. Write mocks by hand.
*   **AssertJ**: Use AssertJ for assertions.
*   **`var` Keyword**: The use of `var` is discouraged.
*   **Immutable Collections**: Prefer immutable collections from Guava over unmodifiable collections from the JDK.
*   **Test Quality**: Maintain the same high quality for test code as for production code.

## Web UI

The Trino Web UI is written in JSX and ES6. To build the UI, you need to have Node.js and Yarn installed.

*   To install dependencies and build the UI, run:
    ```bash
    yarn --cwd core/trino-web-ui/src/main/resources/webapp/src install
    ```
*   If JavaScript dependencies have not changed, you can run a faster build with:
    ```bash
    yarn --cwd core/trino-web-ui/src/main/resources/webapp/src run package
    ```

## Commits and Pull Requests

Follow the [pull request and commit guidelines](https://trino.io/development/process#pull-request-and-commit-guidelines-) when creating commits and pull requests.

## Contributor License Agreement (CLA)

Before your contributions can be accepted, you must sign the [Contributor License Agreement](https://github.com/trinodb/cla).
