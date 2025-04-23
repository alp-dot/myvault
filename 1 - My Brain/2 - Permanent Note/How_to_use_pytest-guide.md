---
tags:
  - python/testing
  - pytest
  - rye
  - development/tools
  - programming/best-practices
---

# Pytest Guide: Project Structure and Organization

## Recommended Project Structure

```
project_root/
│
├── src/
│   └── myproject/
│       ├── __init__.py
│       ├── module1.py
│       └── module2.py
│
├── tests/
│   ├── __init__.py
│   ├── test_module1.py
│   └── test_module2.py
│
├── conftest.py
├── pytest.ini
└── requirements.txt
```

### Folder Structure Explained

1. **`src/` Directory**
   - Contains the actual project source code
   - Keeps production code separate from test code
   - Use a package name (e.g., `myproject`) for better organization

2. **`tests/` Directory**
   - Contains all test files
   - Mirror the structure of the `src/` directory
   - Naming convention: `test_*.py`
   - Each test file corresponds to a source module

3. **`conftest.py`**
   - Shared fixtures and configuration for tests
   - Allows sharing test utilities across multiple test files

4. **`pytest.ini`**
   - Configuration file for pytest
   - Set default behaviors and options

5. **`requirements.txt`**
   - List project dependencies
   - Include pytest and other testing libraries

### Best Practices
- Keep tests close to the code they're testing
- Use descriptive test function names
- Organize tests logically
- Use fixtures for setup and teardown

## Rye Test Command Usage

### Basic Test Execution Modes

1. **Run All Tests**
   ```bash
   rye test
   ```
   - Execute all tests in the project
   - Targets all `test_*.py` files in the `tests/` directory

2. **Run Specific Test File**
   ```bash
   rye test tests/test_module1.py
   ```
   - Run tests from a specific test file
   - Execute all tests within the specified file

3. **Run Specific Test Function**
   ```bash
   rye test tests/test_module1.py::test_specific_function
   ```
   - Run a specific test function
   - Use the format `filename::function_name`

4. **Run Tests in a Module**
   ```bash
   rye test tests/test_module1.py::TestClassName
   ```
   - Execute all tests within a specific test class
   - Run tests at the class level

### Advanced Test Execution Options

5. **Run Tests by Keyword**
   ```bash
   rye test -k "login or authentication"
   ```
   - Run tests containing specific keywords
   - Support multiple keywords with OR condition

6. **Verbose Mode**
   ```bash
   rye test -v
   ```
   - Display more detailed test execution results
   - Show detailed information for each test

7. **Stop on First Failure**
   ```bash
   rye test -x
   ```
   - Stop test execution on the first test failure
   - Useful for debugging

### Tips
- Parallel test execution by default for faster testing
- Measure test coverage possible with `--cov` option
- Customize default behavior via environment variables or configuration files

## References
- [pytest documentation](https://docs.pytest.org/en/latest/)
- [python unittest-guide](https://youtu.be/VaFEuHqwJ80?si=wjYLoo--idmKjok4)
- [[Comprehensive Guide to Pytest Test Discovery and Collection]]