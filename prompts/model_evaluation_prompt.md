## Task Overview

You will evaluate AI-generated code by running unit tests and analyzing the results against four key metrics. The evaluation process involves:

1. **Test Setup**: Update `@temp_tests.py` to match function names in `@temp_code.py` (generated from `@prompt.md`), but I want you to prepare a temp_tests.py file so it has the exact same unit tests as `@tests.py` but that will be run against the code in `@temp_code.py`. Make sure the unit tests are exaxtly the same.
2. **Test Execution**: Run the tests and collect failure logs and error details
3. **Code Analysis**: Evaluate the code against four specific metrics
4. **Documentation**: Add evaluation comments directly to the code

## Step-by-Step Process

### Step 1: Test File Preparation
- Read `@temp_tests.py` and `@temp_code.py`
- Update function names in `@temp_tests.py` to match those in `@temp_code.py`
- Ensure all imports and function calls are correctly aligned
- Note any function name mismatches for inclusion in final evaluation (any function name mismatches is considered as a failer in immplemetation of the prompt)

### Step 2: Test Execution
- Run `@temp_tests.py` to execute all unit tests
- Collect detailed logs of failing tests
- Document all errors, exceptions, a missing function (specially the one that is required by the promt), and test failures
- Analyze the root causes of each failure

### Step 3: Code Evaluation
Evaluate the generated code against these four metrics:


## Evaluation Metrics

### 1. Accuracy
**Question**: Does the AI's response correctly and completely address the information and code requirements?

**Evaluation Criteria**:
- **Factual Correctness**: Are statements and implementations factually accurate?
- **Comprehensive Coverage**: Are all key points and requirements addressed?
- **Code Syntax**: Are there any syntax errors in the generated code?
- **Code Functionality**: Does the code work as intended when executed?

**Severity Levels**:
- **Major Issues**: Critical mistakes that severely impact user experience (little to no value delivered)
- **Moderate Issues**: Significant mistakes that partially affect user experience (some value, but major improvements needed)
- **Minor Issues**: Small mistakes that minimally affect user experience (most value delivered, minor improvements possible)
- **No Issues**: No mistakes found (full optimal value delivered)

**Output Format**: Choose one severity level and provide brief, specific justification.

**Example Justifications**:
- "The model incorrectly stated that JSON is not supported in Python."
- "Accurate and aligns with the user's request."


### 2. Instruction Following
**Question**: Is the provided response on-point and does it respect all constraints in the user prompt? Is it tailored for the user's skill level?

**Evaluation Criteria**:
- **Constraint Adherence**: Does the response follow all specified constraints and requirements?
- **Request Completeness**: Are all user requests addressed? (Exceptions: requests outside LLM capabilities, e.g., "Give me a sorting algorithm with O(log(n)) time complexity")
- **Focus Maintenance**: Does the response stay focused on the user's specific request?
- **Information Balance**: 
  - Not too brief (missing important details)
  - Not too verbose (including unnecessary information)
- **Skill Level Appropriateness**: Is the response tailored to the user's apparent skill level?

**Severity Levels**: Same as Accuracy (Major/Moderate/Minor/No Issues)

**Output Format**: Choose one severity level and provide brief, specific justification.

**Example Justifications**:
- "Response missed key edge case around null input handling."
- "Fully addressed all points from the prompt."

### 3. Efficiency & Optimality
**Question**: Is the AI's response optimal in terms of approach, code complexity, case coverage, and methodology?

**Evaluation Criteria**:
- **Algorithm Efficiency**: 
  - Time and memory complexity optimization
  - Preference for mainstream efficient algorithms over marginally better but complex ones
- **Edge Case Handling**: Does the solution handle all edge cases appropriately?
- **Security Considerations**: Are security aspects of the code properly addressed?
- **Solution Quality**: Does the approach represent the optimal solution for the given problem?

**Severity Levels**: Same as previous metrics (Major/Moderate/Minor/No Issues)

**Output Format**: Choose one severity level and provide brief, specific justification. 

### 4. Other Issues
**Question**: Are there any other significant issues in the response that affect user experience but were not covered in the predefined categories?

**Evaluation Scope**: 
- **Beyond Predefined Categories**: Look for issues not covered by Accuracy, Instruction Following, or Efficiency & Optimality
- **User Experience Impact**: Consider any factor that affects the overall user experience

**Common Examples**:
- Context forgetting in multi-turn conversations
- Poor user interface/experience in provided components
- Overly apologetic tone for limitations
- Inappropriate communication style for the context
- Missing documentation or explanations

**Severity Levels**: Same as previous metrics (Major/Moderate/Minor/No Issues)

**Output Format**: Choose one severity level and provide brief, specific justification.

**Example Justifications**:
- "Tone was overly casual for a professional setting."
- "Response included an unnecessary disclaimer that distracted from the answer."

### 5. Final Score
**Overall Model Rating**: Provide a single numerical score based on the comprehensive evaluation.

**Rating Scale**:
- **5 - Exemplary**: Outstanding performance across all metrics
- **4 - Good**: Strong performance with minor issues
- **3 - Fair**: Adequate performance with some notable issues
- **2 - Bad**: Poor performance with significant issues
- **1 - Terrible**: Severely flawed performance with major issues


## Expected Output Format

Provide your evaluation in the following structured markdown format, so it can be easily copied:

```
Accuracy: [Severity Level]
- [Specific justification with concrete examples]
- [Additional justification if applicable]

Instruction Following: [Severity Level]
- [Specific justification with concrete examples]
- [Additional justification if applicable]

Efficiency & Optimality: [Severity Level]
- [Specific justification with concrete examples]
- [Additional justification if applicable]

Other Issues: [Severity Level]
- [Specific justification with concrete examples]
- [Additional justification if applicable]

Final Score: [1-5] - [Rating Description]
```
**Please note**: Each of the evaluation sections in the above must satsfy the 2 criterias below:
1. They must never sound LLM generated.
2. They should be brief to the point w.r.t `@prompt.md` violations(`Other Issues` can be any). 

**Example Output**:
```
Accuracy: Major Issues
- The code imports `numpy` instead of using the required `os` library, which violates the mandatory constraint for system-level file operations.
- The implementation uses basic Python lists rather than cache-efficient data structures that are explicitly required by the prompt.
- The solution cannot handle datasets exceeding 10^6 elements properly because it loads entire datasets into memory instead of processing them in fixed-size blocks.

Instruction Following: Major Issues
- The response ignores the explicit requirement to use the `os` library for file operations, which represents a fundamental constraint violation.
- The code doesn't address scale limitations for datasets larger than 10^6 elements and fails to process data in fixed-size blocks as required.

Efficiency & Optimality: Major Issues
- The algorithm has O(n) complexity per selection step instead of the required O(log n), making it completely unsuitable for large-scale data processing.
- For datasets with 10^9 elements, the implementation would consume excessive memory and processing time, violating the sub-quadratic performance constraint.

Other Issues: Moderate Issues
- The unauthorized `numpy` import creates an external dependency that could cause failures in constrained environments where only standard libraries are available.
- The implementation has no error handling throughout the codebase, which would cause crashes when encountering unexpected input conditions in production.

Final Score: 1 - Terrible
```
## Code Documentation Requirements

**Additional Task**: Insert evaluation justifications as comments directly into `@temp_code.py`

**Comment Placement Rules**:
- **Specific Line Issues**: Place comments immediately above the problematic line
- **Function-Level Issues**: Place comments immediately above the function definition
- **File-Level Issues**: Place comments at the top of the file
- **Multiple Issues**: Use separate comment blocks for each metric category

**Comment Format**:
```python
# [Metric Name]:
# - [Specific justification]
# - [Additional justification if applicable]
```

**Example Implementation**:
```python
# Accuracy:
# - The code imports `numpy` instead of using the required `os` library, which
#   violates the mandatory constraint for system-level file operations.
#
# Instruction Following:
# - The response ignores the explicit requirement to use the `os` library for
#   file operations, which represents a fundamental constraint violation.
import os
import random
import numpy as np

def initialize_pheromones(length: int) -> list[float]:
    """Initialize pheromones with a small positive value."""
    return [0.1] * length

# Efficiency & Optimality:
# - The heuristic calculation uses simple reciprocals, which is mathematically
#   incorrect for sorting applications and doesn't provide meaningful guidance.
#
# Accuracy:
# - The ant colony optimization logic is too simple and lacks sophisticated
def compute_heuristic(data: list[int]) -> list[float]:
    """Compute heuristic values as 1/value for simplicity."""
    return [1.0 / (val if val != 0 else 1) for val in data]
```

## Important Guidelines

### Output Quality Standards
- **Natural Language**: Write justifications that sound human-written, not AI-generated
- **Conciseness**: Be brief and to the point while maintaining completeness
- **Relevance**: Each bullet point must be directly relevant to its metric category
- **Uniqueness**: Avoid redundancy within each section
- **Grammar**: Ensure perfect grammar and American English conventions
- **Word Count**: Each section should contain 150-200 words total across all bullet points

### Test File Management
- **Source**: `@tests.py` contains unit tests designed for `ideal_code.py`
- **Target**: Create `@temp_tests.py` with identical tests but adapted for `@temp_code.py`
- **Function Name Updates**: If function names don't match, update them in `@temp_tests.py` only
- **Code Modification**: Never edit `@temp_code.py` - only add evaluation comments
- **Failure Documentation**: Document any function name mismatches in the final evaluation

### Content Quality Checklist

Before finalizing your evaluation, review each justification for:
- **Grammar**: Subject-verb agreement, tense consistency, spelling
- **Punctuation**: Proper comma, period, and semicolon usage
- **Article Usage**: Correct use of "a," "an," "the"
- **Style Consistency**: Uniform tone and formality level
- **Sentence Structure**: Clear, readable, appropriately complex sentences
- **Human-like Nuances**: Natural phrasing that doesn't sound AI-generated

**⚠️ CRITICAL REQUIREMENTS**:
- **Natural Language**: Write justifications that sound human-written, not AI-generated
- **Conciseness**: Be brief and to the point while maintaining completeness
- **Exact Format**: Provide your evaluation in the markdown structured format so I can easily copy the text.
- **Code Modification**: Never edit `@temp_code.py` - only add evaluation comments

### File References
- @prompt.md : Contains the original prompt used to generate the code
- @temp_code.py : Contains the AI-generated code to be evaluated
- @temp_tests.py : Contains unit tests adapted for the generated code 