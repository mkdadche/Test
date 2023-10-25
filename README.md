# Python Best Practices

This document outlines best practices for writing Python code in our project. It provides guidelines for maintaining code quality, consistency, and readability.

## Table of Contents

1. [Coding Style](#coding-style)

## Coding Style

Maintaining a consistent coding style is essential for readability and maintainability. We follow the PEP 8 style guide for Python. Key points include:

- **Indentation**: Use 4 spaces for indentation. This makes your code more readable and aligns with the standard Python indentation style. Most code editors and IDEs are configured to automatically use 4 spaces when you press the Tab key.
  
  ```
    def example_function():
        if some_condition:
            do_something()
            do_something_else()
  # Avoid mixing spaces and tabs for indentation.
  ```

- **Line Length**: This helps ensure that your code remains readable without excessive horizontal scrolling. If a line of code exceeds this limit, consider breaking it into multiple lines.
  
  ```
  result = (
      some_long_function_name(arg1, arg2, arg3)
      + another_long_function_name(arg4, arg5)
  )
  
  # Alternatively, use backslashes for line continuation
  result = some_long_function_name(arg1, arg2, arg3) \
      + another_long_function_name(arg4, arg5)

  ```
- **Imports**: Organize imports according to PEP 8 guidelines. Group imports into three sections, with each section separated by a blank line:

    * Standard Library Imports
    * Related Third-Party Imports
    * Local Application/Module Imports
    Additionally, use absolute import paths to ensure clarity.

    ```
    # Good import organization
    import os
    import sys
    
    from my_package import my_module
    from external_library import some_function
    
    from local_module import my_function
    
    # Avoid wildcard imports (e.g., from module import *)

    ```
- **Naming**: Use meaningful and descriptive names for variables, functions, and classes. Follow these naming conventions:

  * Use lowercase with underscores for module and package names (e.g., my_module).
  * Use CamelCase for class names (e.g., MyClass).
  * Use lowercase with underscores for function and variable names (e.g., my_function, my_variable).
    
  ```
  # Good naming conventions
  class MyImportantClass:
      def my_method(self):
          my_variable = 42
  
  # Avoid single-letter variable names or overly generic names (e.g., a, b, x, data)

  ```

- **Function and Method Length**: Keep functions and methods concise and focused on a single responsibility. Ideally, functions should be no longer than a screen's worth of code (roughly 30 lines). If a function becomes too long, consider refactoring it into smaller, more specialized functions.
  
  ```
  # Well-structured function
  def process_data(data):
      cleaned_data = preprocess_data(data)
      result = analyze(cleaned_data)
      return result
  
  # Avoid overly long functions with too many responsibilities.

  ```

- **Type Hinting**: Use type hinting to specify the expected types of variables, function arguments, and return values. This enhances code readability and helps tools like linters and IDEs catch type-related errors.

  ```
  def add_numbers(a: int, b: int) -> int:
    return a + b
  ```

- **Docstrings**: Write descriptive docstrings for modules, classes, functions, and methods. These docstrings serve as documentation for your code, making it easier for others to understand its purpose and usage.

  ```
  def calculate_average(numbers):
      """
      Calculate the average of a list of numbers.
  
      Args:
          numbers (list): A list of numerical values.
  
      Returns:
          float: The average of the numbers.
      """
      # Function implementation
  ```

- **Consistent Naming**: Ensure that your variable names are consistent and follow a logical naming scheme. For example, if you use get_ as a prefix for getter methods, be consistent across your codebase.
  ```
  # Consistency in method naming
  def get_name(self):
      return self._name
  
  # Consistency promotes predictability.
  ```

- **Error Handling**: Handle exceptions gracefully and provide meaningful error messages. Avoid using bare except clauses, which can hide errors. Instead, catch specific exceptions when needed.
  ```
  try:
    result = risky_operation()
  except FileNotFoundError as e:
      log_error(f"File not found: {e}")
  except Exception as e:
      log_error(f"An error occurred: {e}")
    ```

- **List and Dictionary Comprehensions**: Use list comprehensions and dictionary comprehensions for concise and readable code when constructing lists or dictionaries.
  ```
  # List comprehension
  squared_numbers = [x ** 2 for x in numbers]
  
  # Dictionary comprehension
  squared_dict = {key: value ** 2 for key, value in original_dict.items()}
  ```

- **Avoid Global Variables**: Minimize the use of global variables as they can make code less predictable and harder to test. Instead, use function parameters and return values to pass data between functions.
  ```
  # Prefer function parameters and return values over global variables.
  def calculate_total_price(items):
      total_price = 0
      for item in items:
          total_price += item.price
      return total_price

  ```

- **Code Formatting Tools**: `black` code formatting tool and configurations that can our project use to enforce coding style guidelines. For example, if you use `black` for automatic code formatting,

  ```
  use the `black` code formatter to automatically format Python code to adhere to our coding style. To ensure code consistency, please run `black` on your code before submitting a pull request:

  pip install black
  black my_module.py
  ```

- **Linters and Static Analysis**: The `flake8` tool can be used to catch common coding style issues and potential errors.
  ```
  `flake8` as our linter to check for coding style issues, adherence to PEP 8, and other code quality concerns. You can install `flake8` and run it as follows:
  
  pip install flake8
  flake8 my_module.py
  ```

