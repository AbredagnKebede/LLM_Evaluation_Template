I need @prompt.md edited as follow:

1. Avoid asking test cases in the prompt.

2. Explicitly include any hard constraints in the prompt (e.g., data size limits, performance bounds, expected formats). 

3. The prompt must have Sample Input & Output. If not include sample input and output.  

4. The prompt must be written in clear, natural human language not AI-generated. It must not have any non-ascii characters in it as well. Replace all of such characters with ascii versions or remove them if they can't be replaced. 

5. The function signiture section should have all import statements and function signitures for helper function the main function is going to use. Aviod using data structures from typing module unless explicitly required, use the built in list, tuple...etc instead. 

Here is the metadata for the task:

```
Task difficult: Easy
```

Make sure the final prompt satisfies the following requirements based on the metadata:
- Refer to the 'Task Difficulty' in the metadata section of the task. This indicates the difficulty of the prompt for the model, which loosely guides the prompt design. Difficulty encompasses not only the complexity of the problem but also the number of requirements included in the prompt. We can judge whether a response is easy, medium, or hard by whether it contains at least one of the following properties: 
   - Hard: Prompt with 8+ constraints or 150+ lines of code or a FANG principle engineer can solve the problem within 1 hour 
   - Medium: Prompt with 4-7 constraints or 50-149 lines of code or a FANG senior engineer can solve the problem within 1 hour 
   - Easy: Prompt with <=3 constraints or 1-49 lines of code or a FANG entry/mid engineer can solve the problem within 1 hour 
Now, based on the given conditions, check how the prompt aligns with the difficulty.

- Refer to the metadata for the task. The prompt should contain the requirement or code related to the programming language specified in the 'Programming Language' section of the metadata. This strictly guides the design of the user prompts. Give a boolean score 0 or 1 based on the evaluation result. For the cases, where the programming language is not specified in user prompt, understand the context from previous turns. The first turn prompt must have specifications about the programming language.

- Refer to the 'L1 Taxonomy' and 'L2 Taxonomy' in the metadata section of the task. This strictly guides the nature/theme of the user prompt. The user prompt should strictly match the given taxonomy. L1 Taxonomy: A hierarchical classification of topics that will be strictly followed, where each level represents a broader or more specific category. For example, "Backend Development > API Development" represents a broader category (Backend) and a specific focus (API Development). L2 Taxonomy: A focused subject derived from the taxonomy that will be strictly followed to narrow down the discussion. For example, "Python-based Microservice Architecture in Backend" is a subtopic under API Development.

- Refer to the 'Conversation Type' in the metadata section of the task. Conversation can belong to any of the given three categories: 1. Coding Tasks: Tasks that test the general coding ability of the model. All the following tasks are single turn only. Conversations: Code Generation: A natural language request that requires the creation of code and can optionally include helper functions and empty function bodies. Please refer to this link for additional instructions. Code Completion: Function body with the description of the problem in the docstring. Can optionally include a set of test cases. These test cases can either be written in doctest format or descriptive format. Please refer to this link for additional instructions. Code Fixing: A request in natural language to fix the given erroneous code snippet. Please refer to this link for additional instructions. Test-case Generation: A request in natural language to generate test cases for a given code snippet. Please refer to this link for additional instructions. Output Generation: A request in natural language to predict the output for the given code snippet for a given input. Code Explanation: A request in natural language to generate an explanation for the given code snippet. 2. General Tasks: In these tasks, you should curate samples of the code-generation type, where the task is to generate a code snippet given a natural-language request as input. Please refer to this link for detailed instructions. Web/Mobile Development: A request in natural language to generate front-end, backend, and helper functions to develop a standalone web application. ML Engineering: A request in natural language to generate code snippets to process given data or code snippets to train and test user-specified model or inference code to generate output from the given model type. Please refer to this link for additional instructions. 3. Special Tasks: These tasks will focus on CoT (Chain of Thought) and Multi-turn. Please refer to this link for detailed instructions. CoT (Chain of Thought): A natural language request that requires the creation of code and can optionally include helper functions and empty function bodies. Multi-turn: A natural language request that requires the creation of code and can optionally include helper functions and empty function bodies. So, each category has its own conversation type.


Notes:
- The goal of all this edits is to make the prompt hareder for target LLM to completely abide with it in an aim to understand the model's limitation
- Don't be too verbose or too complicated. It should be hard enought to break the model. 
- Check for ambiguous or contradicatory statements and fix them iteratively 
- Aim for minimal edits i.e. edit only what needs to be editied according to the guidelines above otherwise try to keep the original content.
- The code block in the function signiture must contain all function signitures which the ideal implementation would have. So if you were going to do the task, how would the code structure would look like? Think of that ideal code and the function signiture should have the imports and the signitures there. 
- Please make sure the prompt is contradiction free and does not include any impossible constraint in it.