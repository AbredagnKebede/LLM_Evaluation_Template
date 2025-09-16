# Prompt Enhancement Instructions

Please edit the `@prompt.md` file according to the following requirements:

## Core Requirements

### 1. Test Case Exclusion
- **DO NOT** include requests for test case generation in the prompt
- Focus on the main problem solution only

### 2. Constraints Specification
- **MUST** explicitly state all hard constraints including:
  - Data size limits (e.g., "input array size ≤ 10^6")
  - Performance bounds (e.g., "time complexity O(n log n)")
  - Expected output formats (e.g., "return as list of integers")
  - Memory constraints (e.g., "use O(1) extra space")

### 3. Sample Input & Output
- **MUST** include at least one complete example with:
  - Clear input format
  - Expected output format
  - Step-by-step explanation if complex

### 4. Language Quality
- Write in **clear, natural human language**
- **NO AI-generated sounding phrases**
- **NO non-ASCII characters** - replace with ASCII equivalents or remove
- Use simple, direct sentences

### 5. Function Signature Requirements
- Include **ALL** import statements needed
- Include **ALL** function signatures for helper functions
- **AVOID** typing module (List, Tuple, etc.) unless explicitly required
- Use built-in types: `list`, `tuple`, `dict`, `set` instead 

## Task Metadata

```
Topic: Algorithmic Paradigms & Patterns

Subtopic: Sqrt Decomposition

Use Case: Develop a production-ready aviation systems implementation using random for General use cases

Task Difficulty: Easy

Programming Language: Python

L1 Taxonomy >> L2 Taxonomy

Advanced Algorithms >> Approximation Algorithms
```

## Metadata-Based Requirements
### Programming Language Specification
- **MUST** specify the programming language clearly in the prompt
- Include language-specific syntax and conventions
- Use appropriate data structures and idioms for the language

### Taxonomy Alignment
- **L1 Taxonomy**: Broad category (e.g., "Backend Development")
- **L2 Taxonomy**: Specific focus (e.g., "API Development")
- Ensure prompt content strictly matches the given taxonomy classification

### Conversation Type Categories

#### 1. Coding Tasks (Single Turn)
- **Code Generation**: Natural language request for code creation
- **Code Completion**: Function body with problem description in docstring
- **Code Fixing**: Fix erroneous code snippet
- **Test-case Generation**: Generate test cases for given code
- **Output Generation**: Predict output for given code and input
- **Code Explanation**: Explain given code snippet

#### 2. General Tasks
- **Web/Mobile Development**: Generate frontend, backend, helper functions
- **ML Engineering**: Data processing, model training, inference code

#### 3. Special Tasks
- **CoT (Chain of Thought)**: Code creation with reasoning steps
- **Multi-turn**: Code creation across multiple interactions


## Implementation Guidelines

### Quality Standards
- **Goal**: Create prompts that challenge LLM capabilities to understand model limitations
- **Balance**: Make it challenging but not overly complex or verbose
- **Clarity**: Eliminate ambiguous or contradictory statements through iterative review
- **Minimalism**: Edit only what's necessary - preserve original content when possible

### Function Signature Design
- **Complete Structure**: Include ALL function signatures that an ideal implementation would require
- **Import Statements**: Add all necessary imports at the top
- **Helper Functions**: Include signatures for any helper functions the main function will use
- **Think Ahead**: Consider the complete code structure you would write to solve this problem

### Validation Checklist
- [ ] No contradictory requirements
- [ ] No impossible constraints
- [ ] Clear, unambiguous language
- [ ] Appropriate difficulty level
- [ ] Complete function signatures
- [ ] Sample input/output included
- [ ] Hard constraints specified
- [ ] Programming language specified
- [ ] Taxonomy alignment verified

## Action Items
1. Read the current `@prompt.md` file
2. Apply all requirements above systematically
3. Validate against the checklist
4. Ensure the enhanced prompt is ready for LLM evaluation