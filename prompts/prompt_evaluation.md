I need you to use @prompt.md as the sole context to generate the following deliverables. Do not leave any field empty in your outputs; if a field is genuinely not applicable, write "None" (as a literal string) instead of leaving it blank.

1. Python docstring: This is the Python docstring version of @prompt.md for each function signature found in @prompt.md. Use the following structure and ensure every section is present and non-empty (use "None" only if truly not applicable):

```python
import itertools
from random import shuffle

def task_func(numbers=list(range(1, 11))):
    """
    Calculates the average of the sums of absolute differences between each pair of consecutive numbers
    for all permutations of a given list. Each permutation is shuffled before calculating the differences.

      Parameters:
      - numbers (list): A list of numbers. Default is numbers from 1 to 10.

      Returns:
      - float: The average of the sums of absolute differences for each shuffled permutation of the list.

      Requirements:
      - itertools
      - random.shuffle

      Raises:
      - TypeError: numbers must be an iterable of numeric values.
      - ValueError: numbers must not be empty.

      Example:
      >>> result = task_func([1, 2, 3])
      >>> isinstance(result, float)
      True
    """
```

2. Doc Struct (JSON): For each function signature found in @prompt.md, provide a JSON object that mirrors the sections present in the Python docstring (the JSON must contain the same fields that appear in the docstring: description, parameters, returns, requirements, raises, examples). Use the following structure and ensure all arrays contain at least one item (use "None" only if truly not applicable):

```json
{
  "description": [
    "Calculates the average of the sums of absolute differences between each pair of consecutive numbers.",
    "For all permutations of a given list. Each permutation is shuffled before calculating the differences."
    "params":,
    "- numbers (list): A list of numbers. Default is numbers from 1 to 11."
  ],
  "Args": [
    "- numbers (list): A list of numbers. Default is numbers from 1 to 11."
  ],
  "returns": [
    "- float: The average of the sums of absolute differences for each shuffled permutation of the list."
  ],
  "reqs": [
    "itertools",
    "random.shuffle"
  ],
  "raises": [
    "TypeError: numbers must be an iterable of numeric values.",
    "ValueError: numbers must not be empty."
  ],
  "examples": [
    ">>> result = task_func([1, 2, 3])",
    ">>> isinstance(result, float)",
    "True"
  ]
}
```

For the following items, provide a single aggregated answer for the entire prompt (i.e., do NOT answer per function; answer once for the whole @prompt.md):

3. How many constraints are present in @prompt.md?
4. How complex is the overall topic? Choose exactly one from [Highschool, Undergraduate, Graduate, PHD and above].
5. Does @prompt.md address the real-world use case? Use case: "********USE CASE*******". Answer Yes or No and briefly justify.
6. Sample Input: Provide a representative input for the entire prompt in a code block.
7. Sample Output: Provide the corresponding representative output for the entire prompt in a code block.


Notes:
- Please follow the provided formats strictly. Don't add fields beyond those specified.
- We don't use typing annotations like List or Tuple. Use built-in list, tuple, etc.
- No ambiguous or contradictory contents.
- Examples must be derived from @prompt.md.
- Produce the Python docstring and Doc Struct JSON for each function signature in @prompt.md.
- Items 3–7 are aggregated for the entire prompt, not per-function.



For example here is what the the input and output looks like:

INPUT:

```markdown
Consider a sports analytics system where data processing and optimization form the backbone of performance evaluation. In this system, large-scale data, ranging from 10^6 to 10^9 elements, needs to be efficiently processed and analyzed to extract meaningful insights. The system needs to leverage Cache-Optimized Ant Colony Optimization (ACO) techniques to achieve fast and efficient search operations, especially under conditions of high data volume and tight performance constraints. This task involves complex trade-offs where memory usage and processing speed must be balanced effectively.

### Objectives
1. **Design** a cache-efficient data structure to store and manage sports analytics data that underpins the Ant Colony Optimization algorithm.
2. **Implement** an Ant Colony Optimization algorithm using the `os` library to handle file operations and manage system resources efficiently.
3. **Develop** a cache-optimization strategy that minimizes cache misses and enhances data retrieval speed while processing large datasets.
4. **Create** a simulation environment to model the behavior of ants as they search for optimal paths in a data set.
5. **Build** a mechanism to dynamically adjust pheromone levels based on solution quality and search efficiency.
6. **Optimize** per-step selection and data access to O(log n) amortized; ensure total runtime for sorting-scale workloads is O(n log n) or better and remains sub-quadratic for all n.
7. **Engineer** a robust testing framework to validate the accuracy and performance of the algorithm across varying data scales.

### Constraints
- **Performance Requirements**: Achieve O(log n) amortized time for selection/lookup steps and O(n log n) or better total runtime for full runs on sorting-scale tasks. The design must remain sub-quadratic for all n and degrade gracefully up to 10^9 elements.
- **Scale Limitations**: Must handle inputs up to 10^9 elements. For n > 10^6, do not load the entire dataset into memory; process in fixed-size blocks using `os` file operations.
- **Library-Specific Constraints**: Utilize the `os` library for managing file operations and system-level resource usage.


### Function Signature
```python
import os
import random

def initialize_pheromones(length: int) -> list[float]:
    ...

def compute_heuristic(data: list[int]) -> list[float]:
    ...

def choose_next_index(current_index: int, candidates: list[int], pheromones: list[float], heuristic: list[float]) -> int:
    ...

def update_pheromones(pheromones: list[float], path: list[int], decay: float, deposit: float) -> None:
    ...

def cache_optimized_aco(data: list[int], num_ants: int, iterations: int) -> list[int]:
    pass
```

### Sample Input/Output
- **Sample Input**: `[3, 5, 1, 8, 9, 2, 4, 7, 6]`, `num_ants=100`, `iterations=1000`
- **Expected Output**: `[1, 2, 3, 4, 5, 6, 7, 8, 9]`  
This output represents the optimal sorted order of elements based on ant colony path finding.

### Expected Output Format
- **Description**: The function should return a list of integers representing the optimized order of elements as determined by the Cache-Optimized Ant Colony Optimization algorithm. The list should be sorted in ascending order based on the algorithm's path finding results.
```

OUTPUT:

```
Python docstrings:

```python
import os
import random

def initialize_pheromones(length):
    """
    Initializes the pheromone levels for an Ant Colony Optimization (ACO) run over a dataset,
    sized to the number of selectable elements. Designed to support cache-aware traversal at scale.

      Parameters:
      - length (int): Number of elements requiring initial pheromone values. Must be >= 1.

      Returns:
      - list: A list of float pheromone levels of size equal to length.

      Requirements:
      - os
      - random

      Raises:
      - TypeError: length must be an int.
      - ValueError: length must be >= 1.

      Example:
      >>> pher = initialize_pheromones(5)
      >>> len(pher) == 5
      True
    """


def compute_heuristic(data):
    """
    Computes heuristic desirability values used by ACO to bias selection toward promising elements.
    Heuristics should be cache-friendly to compute and reuse, supporting O(log n) amortized selection.

      Parameters:
      - data (list): List of integers representing the dataset to evaluate.

      Returns:
      - list: A list of float heuristic values aligned index-wise with data.

      Requirements:
      - os
      - random

      Raises:
      - TypeError: data must be a list of integers.
      - ValueError: data must not be empty.

      Example:
      >>> heur = compute_heuristic([3, 1, 2])
      >>> isinstance(heur, list) and len(heur) == 3
      True
    """

def update_pheromones(pheromones, path, decay, deposit):
    """
    Updates pheromone levels along a discovered path using decay and deposit rules.
    Supports dynamic adjustment to reinforce good solutions while avoiding stagnation.

      Parameters:
      - pheromones (list): Mutable list of current pheromone levels to be updated in place.
      - path (list): Sequence of indices visited by an ant or best-known path.
      - decay (float): Evaporation rate in [0.0, 1.0], where higher removes more pheromone.
      - deposit (float): Amount added along the path to reinforce solution quality. Must be >= 0.

      Returns:
      - None: Pheromone levels are modified in place.

      Requirements:
      - os
      - random

      Raises:
      - TypeError: Invalid types for pheromones, path, decay, or deposit.
      - ValueError: decay must be in [0.0, 1.0]; deposit must be >= 0; path must not be empty.

      Example:
      >>> ph = [0.1] * 5
      >>> update_pheromones(ph, [0, 2, 4], 0.1, 0.05)
      >>> isinstance(ph, list) and len(ph) == 5
      True
    """ 

def cache_optimized_aco(data, num_ants, iterations):
    """
    Executes a cache-optimized Ant Colony Optimization to produce an optimized ordering of data,
    targeting O(log n) amortized selection and O(n log n) total runtime on sorting-scale tasks,
    and using block-based file operations via os for very large inputs.

      Parameters:
      - data (list): List of integers to optimize (e.g., sort via ACO-based path finding).
      - num_ants (int): Number of ants per iteration. Must be >= 1.
      - iterations (int): Number of iterations to run. Must be >= 1.

      Returns:
      - list: Optimized list of integers, expected to be in ascending order for sorting-style tasks.

      Requirements:
      - os
      - random

      Raises:
      - TypeError: Invalid types for data, num_ants, or iterations.
      - ValueError: data must not be empty; num_ants and iterations must be >= 1.

      Example:
      >>> result = cache_optimized_aco([3, 5, 1, 8, 9, 2, 4, 7, 6], 100, 1000)
      >>> isinstance(result, list) and result == sorted([3, 5, 1, 8, 9, 2, 4, 7, 6])
      True
    """
```

Doc Struct (JSON): 

```json
{
  "function": "initialize_pheromones",
  "description": [
    "Initializes pheromone levels for ACO across a fixed number of elements.",
    "Designed to support cache-aware traversal and scalable runs."
  ],
  "Args": [
    "- length (int): Number of elements to initialize. Must be >= 1."
  ],
  "returns": [
    "- list: Float pheromone levels with length equal to length."
  ],
  "reqs": [
    "os",
    "random"
  ],
  "raises": [
    "TypeError: length must be an int.",
    "ValueError: length must be >= 1."
  ],
  "examples": [
    ">>> pher = initialize_pheromones(5)",
    ">>> len(pher) == 5",
    "True"
  ]
}

{
  "function": "compute_heuristic",
  "description": [
    "Computes heuristic desirability values that bias ACO selection toward promising elements.",
    "Heuristics should be efficient and cache-friendly for O(log n) amortized selection."
  ],
  "Args": [
    "- data (list): List of integers comprising the dataset."
  ],
  "returns": [
    "- list: Float heuristic values aligned with indices of data."
  ],
  "reqs": [
    "os",
    "random"
  ],
  "raises": [
    "TypeError: data must be a list of integers.",
    "ValueError: data must not be empty."
  ],
  "examples": [
    ">>> heur = compute_heuristic([3, 1, 2])",
    ">>> isinstance(heur, list) and len(heur) == 3",
    "True"
  ]
}
 


{
  "function": "choose_next_index",
  "description": [
    "Selects the next index for an ant based on pheromone and heuristic values over candidates.",
    "Aims for efficient, cache-aware selection with O(log n) amortized behavior."
  ],
  "Args": [
    "- current_index (int): Current position of the ant.",
    "- candidates (list): Non-empty list of candidate indices.",
    "- pheromones (list): Pheromone levels for all indices.",
    "- heuristic (list): Heuristic values for all indices."
  ],
  "returns": [
    "- int: The chosen next index from candidates."
  ],
  "reqs": [
    "os",
    "random"
  ],
  "raises": [
    "TypeError: Invalid types for inputs.",
    "ValueError: candidates must not be empty; pheromones and heuristic must align with indices."
  ],
  "examples": [
    ">>> idx = choose_next_index(0, [1, 2, 3], [0.5, 0.5, 0.5, 0.5], [1.0, 0.8, 0.9, 0.7])",
    ">>> idx in [1, 2, 3]",
    "True"
  ]
}

{
  "function": "update_pheromones",
  "description": [
    "Applies decay and deposit to update pheromone levels along a path.",
    "Reinforces good solutions while avoiding stagnation via evaporation."
  ],
  "Args": [
    "- pheromones (list): Mutable list of pheromone levels updated in place.",
    "- path (list): Sequence of visited indices.",
    "- decay (float): Evaporation rate in [0.0, 1.0].",
    "- deposit (float): Non-negative amount added along the path."
  ],
  "returns": [
    "- None: Updates occur in place."
  ],
  "reqs": [
    "os",
    "random"
  ],
  "raises": [
    "TypeError: Invalid types for pheromones, path, decay, or deposit.",
    "ValueError: decay must be in [0.0, 1.0]; deposit must be >= 0; path must not be empty."
  ],
  "examples": [
    ">>> ph = [0.1] * 5",
    ">>> update_pheromones(ph, [0, 2, 4], 0.1, 0.05)",
    ">>> isinstance(ph, list) and len(ph) == 5",
    "True"
  ]
} 




{
  "function": "cache_optimized_aco",
  "description": [
    "Runs a cache-optimized ACO to produce an optimized ordering of the data.",
    "Targets O(log n) amortized selection and O(n log n) total runtime; uses os for block-based IO at large scales."
  ],
  "Args": [
    "- data (list): List of integers to optimize.",
    "- num_ants (int): Number of ants per iteration, >= 1.",
    "- iterations (int): Number of iterations, >= 1."
  ],
  "returns": [
    "- list: Optimized ordering of data, expected ascending for sorting-style tasks."
  ],
  "reqs": [
    "os",
    "random"
  ],
  "raises": [
    "TypeError: Invalid types for data, num_ants, or iterations.",
    "ValueError: data must not be empty; num_ants and iterations must be >= 1."
  ],
  "examples": [
    ">>> result = cache_optimized_aco([3, 5, 1, 8, 9, 2, 4, 7, 6], 100, 1000)",
    ">>> isinstance(result, list) and result == sorted([3, 5, 1, 8, 9, 2, 4, 7, 6])",
    "True"
  ]
}
```
How many constraints: 3
Complexity: Graduate
Real-world use case “USE CASE”: Yes — it models large-scale sports analytics optimization with cache-aware ACO and system-level IO.

Sample Input:
```python
data = [3, 5, 1, 8, 9, 2, 4, 7, 6]
num_ants = 100
iterations = 1000
# result = cache_optimized_aco(data, num_ants, iterations)
```

Sample Output:
```python
[1, 2, 3, 4, 5, 6, 7, 8, 9]
```

```     