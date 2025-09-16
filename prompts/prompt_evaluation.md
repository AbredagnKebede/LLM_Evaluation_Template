# LLM Code Evaluation and Documentation Generation Task

## 🎯 **TASK OVERVIEW**
You are tasked with analyzing a provided code prompt (`@prompt.md`) and generating comprehensive documentation and evaluation metrics. This task requires you to extract function signatures, create detailed documentation, and provide analytical insights about the code's complexity and real-world applicability.

## 📋 **REQUIRED DELIVERABLES**

### **1. Python Docstring Generation**
For **each function signature** found in `@prompt.md`, generate a complete Python docstring following this exact structure:

```python
import library1
import library2

def function_name(param1: type, param2: type = default_value) -> return_type:
    """
    [Clear, concise description of what the function does and its purpose]

      Parameters:
      - param1 (type): Description of parameter 1. Include constraints if any.
      - param2 (type): Description of parameter 2. Include default behavior if applicable.

      Returns:
      - return_type: Description of what the function returns and its format.

      Requirements:
      - library1
      - library2

      Raises:
      - ExceptionType: Description of when this exception is raised.
      - AnotherException: Description of when this exception is raised.

      Example:
      >>> result = function_name(example_input)
      >>> isinstance(result, expected_type)
      True
    """
```

**CRITICAL REQUIREMENTS:**
- ✅ Include all import statements from the prompt at the top of the code block
- ✅ Function signatures MUST include type hints (e.g., `value: str -> int`)
- ✅ Every section must be present and non-empty
- ✅ If a section is genuinely not applicable, write "None" (as literal string)
- ✅ Use built-in types (list, tuple, dict) - NOT typing annotations (List, Tuple, Dict)
- ✅ Examples must be derived from the actual prompt content

### **2. Documentation Structure (JSON)**
For **each function signature** found in `@prompt.md`, provide a JSON object that mirrors the docstring sections:

```json
{
  "function_name": {
    "description": [
      "First line of function description",
      "Second line of function description if needed"
    ],
    "Args": [
      "- param1 (type): Description of parameter 1",
      "- param2 (type): Description of parameter 2"
    ],
    "returns": [
      "- return_type: Description of return value"
    ],
    "reqs": [
      "library1",
      "library2"
    ],
    "raises": [
      "ExceptionType: Description of exception condition",
      "AnotherException: Description of exception condition"
    ],
    "examples": [
      ">>> result = function_name(example_input)",
      ">>> isinstance(result, expected_type)",
      "True"
    ]
  }
}
```

**CRITICAL REQUIREMENTS:**
- ✅ All arrays must contain at least one item
- ✅ Use "None" only if truly not applicable
- ✅ JSON structure must exactly match docstring sections

### **3. Prompt Analysis (Aggregated for Entire Prompt)**
Provide a single comprehensive analysis for the entire `@prompt.md`:

#### **3.1 Constraint Count**
Count and report the total number of constraints present in the prompt.

#### **3.2 Complexity Assessment**
Evaluate the overall topic complexity and select exactly one from:
- `Highschool`
- `Undergraduate` 
- `Graduate`
- `PHD and above`

#### **3.3 Real-World Use Case Evaluation**
Determine if the prompt addresses a real-world use case. Use case: "********USE CASE*******". Answer format:
- **Answer:** Yes or No
- **Justification:** Brief explanation of why it does or doesn't address real-world applications

#### **3.4 Sample Input**
Provide a representative input for the entire prompt in a code block:
```python
# Example input that demonstrates the prompt's functionality
```

#### **3.5 Sample Output**
Provide the corresponding representative output in a code block:
```python
# Expected output that matches the sample input
```

## 🔧 **TECHNICAL SPECIFICATIONS**

### **Type Hint Requirements**
- ✅ **MANDATORY:** All function signatures must include type hints
- ✅ Use built-in types: `list[int]`, `dict[str, float]`, `tuple[str, int]`
- ✅ **FORBIDDEN:** Do not use `List`, `Tuple`, `Dict` from typing module
- ✅ Include return type annotations: `-> return_type`

### **Content Quality Standards**
- ✅ **No Ambiguity:** All descriptions must be clear and unambiguous
- ✅ **No Contradictions:** Ensure all information is internally consistent
- ✅ **Derived Examples:** All examples must be based on actual prompt content
- ✅ **Complete Coverage:** Address every function signature found in the prompt

### **Format Compliance**
- ✅ **Strict Adherence:** Follow provided formats exactly
- ✅ **No Additional Fields:** Do not add fields beyond those specified
- ✅ **Consistent Structure:** Maintain consistent formatting throughout

## 📝 **WORKFLOW INSTRUCTIONS**

1. **Read and Analyze:** Carefully examine `@prompt.md` to identify all function signatures and import statements
2. **Extract Information:** For each function, extract parameters, return types, requirements, and all imports
3. **Generate Docstrings:** Create comprehensive docstrings with imports at the top, following the exact template
4. **Create JSON Structure:** Generate corresponding JSON documentation for each function
5. **Analyze Prompt:** Provide aggregated analysis for the entire prompt
6. **Validate Output:** Ensure all requirements are met, imports are included, and no fields are empty

## 🚫 **COMMON PITFALLS TO AVOID**

- ❌ **Missing Imports:** Not including import statements from the prompt
- ❌ **Missing Type Hints:** Function signatures without type annotations
- ❌ **Empty Fields:** Leaving any required field blank
- ❌ **Wrong Type Annotations:** Using `List` instead of `list`
- ❌ **Inconsistent Examples:** Examples not derived from actual prompt
- ❌ **Incomplete Analysis:** Missing any of the 5 analysis components
- ❌ **Format Deviations:** Not following the exact specified formats

## 📊 **EXAMPLE WORKFLOW**

### **Input Analysis:**
```markdown
# Example prompt content with function signatures
import os
import random
import itertools

def initialize_data(size: int) -> list[float]:
    ...

def process_data(data: list[float], factor: float = 1.0) -> list[float]:
    ...

def analyze_results(results: list[float]) -> dict[str, float]:
    ...
```

### **Expected Output Structure:**

```python
import os
import random
import itertools

def initialize_data(size: int) -> list[float]:
    """
    [Generated docstring for initialize_data following exact template]
    """

def process_data(data: list[float], factor: float = 1.0) -> list[float]:
    """
    [Generated docstring for process_data following exact template]
    """

def analyze_results(results: list[float]) -> dict[str, float]:
    """
    [Generated docstring for analyze_results following exact template]
    """
```

```json
{
  "initialize_data": {
    "description": [...],
    "Args": [...],
    "returns": [...],
    "reqs": [...],
    "raises": [...],
    "examples": [...]
  },
  "process_data": {
    "description": [...],
    "Args": [...],
    "returns": [...],
    "reqs": [...],
    "raises": [...],
    "examples": [...]
  },
  "analyze_results": {
    "description": [...],
    "Args": [...],
    "returns": [...],
    "reqs": [...],
    "raises": [...],
    "examples": [...]
  }
}
```

**Analysis Results:**
- Constraints: [number]
- Complexity: [level]
- Real-world use case: [Yes/No with justification]
- Sample Input: [code block]
- Sample Output: [code block]

---

## 🎯 **FINAL REMINDER**
Your task is to transform `@prompt.md` into comprehensive, well-structured documentation while providing analytical insights. Every function signature must be documented, every field must be completed, and every requirement must be met. Focus on clarity, completeness, and adherence to the specified formats.