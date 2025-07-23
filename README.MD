# Python Lambda Examples

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![License](https://img.shields.io/badge/License-MIT-green)
![Status](https://img.shields.io/badge/Status-Active-brightgreen)

## Overview

**Python Lambda Examples** is a repository featuring an [IPython notebook](lambda_best_practices.ipynb) that demonstrates best practices for using **lambda functions** in Python. The notebook covers a variety of use cases, including basic arithmetic, conditional logic, functional programming with `map`, `filter`, and `reduce`, sorting, nested lambdas, and data manipulation with `pandas`. This project is ideal for Python developers, data scientists, and learners exploring the power and flexibility of lambda functions.

## Table of Contents

- [Features](#features)
- [Getting Started](#getting-started)
- [Usage Examples](#usage-examples)
- [Best Practices](#best-practices)
- [Dependencies](#dependencies)
- [Contributing](#contributing)
- [License](#license)

## Features

- **Comprehensive Examples**: Includes basic lambda syntax, conditional checks (e.g., even/odd, positive/negative/zero), and string manipulations.
- **Functional Programming**: Showcases `map`, `filter`, and `reduce` for transforming, filtering, and aggregating data.
- **Data Manipulation**: Demonstrates `pandas` usage for tasks like converting names to initials and assigning grades based on scores.
- **Sorting and Nested Lambdas**: Covers custom sorting of tuples and dictionaries, as well as advanced nested lambda functions.
- **Real-World Applications**: Applies lambdas to scenarios like formatting numbers, filtering aircraft names by length, and finding the longest string.

## Getting Started

### Prerequisites

- Python 3.8 or higher
- Jupyter Notebook or JupyterLab
- Required Python packages (see [Dependencies](#dependencies))

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/python-lambda-examples.git
   cd python-lambda-examples
   ```

2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

3. Launch Jupyter Notebook:
   ```bash
   jupyter notebook lambda_functions.ipynb
   ```

### Creating requirements.txt

To support the installation, create a `requirements.txt` file with:
```text
pandas
```

## Usage Examples

The [lambda_functions.ipynb](lambda_functions.ipynb) notebook includes the following examples:

1. **Checking Even or Odd Numbers**:
   ```python
   check_even = lambda x: "Even" if x % 2 == 0 else "Odd"
   print(check_even(10))  # Output: Even
   ```

2. **Mapping Names with Prefix**:
   ```python
   names = ["max", "tax", "jax", "rex", "bix"]
   capitalized_names = list(map(lambda x: "Hello " + str(x).capitalize(), names))
   print(capitalized_names)  # Output: ['Hello Max', 'Hello Tax', 'Hello Jax', 'Hello Rex', 'Hello Bix']
   ```

3. **Filtering Strings by Length**:
   ```python
   aircrafts = ["Supermarine Spitfire", "Messerschmitt Bf 109", "North American P-51 Mustang", "Focke-Wulf Fw 190", "Mitsubishi A6M Zero"]
   filtered_aircrafts = list(filter(lambda x: len(x) >= 20, aircrafts))
   print(filtered_aircrafts)  # Output: ['North American P-51 Mustang']
   ```

4. **Reducing to Find Longest String**:
   ```python
   furniture_brands = ["IKEA", "Ashley Furniture", "Ethan Allen", "La-Z-Boy", "Herman Miller"]
   longest_string = reduce(lambda x, y: x if len(x) > len(y) else y, furniture_brands)
   print(longest_string)  # Output: Ashley Furniture
   ```

5. **Pandas Data Transformation**:
   ```python
   df_writers = pd.DataFrame(["J.R.R. Tolkien", "George R.R. Martin", "Brandon Sanderson"], columns=["Fantasy Authors"])
   df_writers["Name Initials"] = df_writers["Fantasy Authors"].apply(lambda x: x.split()[0][0] + "." + x.split()[1][0])
   print(df_writers)
   ```

6. **Sorting Tuples by Multiple Keys**:
   ```python
   tuples = [("a", 2), ("b", 3), ("c", 2)]
   sorted_tuples = sorted(tuples, key=lambda x: (-x[1], x[0]))
   print(sorted_tuples)  # Output: [('b', 3), ('a', 2), ('c', 2)]
   ```

7. **Number Formatting with Commas**:
   ```python
   format_number = lambda x: f"{x:,}"
   print(format_number(1000000))  # Output: '1,000,000'
   ```

Explore the notebook for additional examples, including nested lambdas and sorting dictionaries by values.

## Best Practices

The notebook adheres to several lambda function best practices:
- **Single Expressions**: All lambdas are concise, single-expression functions.
- **Functional Programming**: Uses `map`, `filter`, and `reduce` for declarative code.
- **Contextual Use**: Applies lambdas for one-off tasks like sorting keys and data transformations.
- **Readability**: Includes descriptive variable names and clear examples.

**Recommendations for Improvement**:
- Add error handling for edge cases (e.g., invalid string splits or empty lists).
- Optimize redundant computations, such as reusing `x.split()` in pandas lambdas:
  ```python
  df_writers["Name Initials"] = df_writers["Fantasy Authors"].apply(
      lambda x: (parts := x.split())[0][0] + "." + parts[1][0] if len(parts) >= 2 else parts[0]
  )
  ```
- Use list comprehensions for simple transformations to improve performance.
- Follow PEP 8 naming conventions (e.g., `filtered_aircrafts` instead of `filetAir`).
- Correct typos (e.g., `"Negetive"` to `"Negative"` in `check_posnag`).
- Add comments for complex lambdas to enhance clarity.

## Dependencies

The notebook requires the following Python libraries:
- `pandas`: For data manipulation and analysis.
- `functools`: For the `reduce` function.

Install them using:
```bash
pip install pandas
```

## Contributing

Contributions are welcome! To contribute:
1. Fork the repository.
2. Create a new branch (`git checkout -b feature/your-feature`).
3. Make your changes and commit (`git commit -m "Add your feature"`).
4. Push to the forked repository (`git push origin feature/your-feature`).
5. Open a pull request.

Please ensure your code follows PEP 8 guidelines and includes relevant comments.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

Happy coding with lambda functions! 🚀