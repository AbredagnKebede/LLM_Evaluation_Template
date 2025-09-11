I need you to prepare an ideal code which follows all requirements, instructions and eveything that is in @prompt.md inside @ideal_code.py 

Refine the code by testing it with @tests.py untill it's passess all the tests. 

Beside the ideal code, I also need the followings generated in the chat:
 
1. Test Dependencies: external dependencies used by  the tests in json format. for example:
```json
{
  "module_name": "exact version",
  "module_name": "exact version"
}
```

2. Libs: All dependencies(external/built-in) of the ideal code inside a list for example: ['numpy', 'random', 'math']

3. Line and Branch coverage of the test.

Notes:
- Ensure Line and Branch Coverage ≥ 90%. If any of them are below 90%, update the ideal code. But make sure the ideal code passess all the tests when you make a change. Use coverage python module to verify that. 
- While running the tests, use a virtual enviroment that is already inside the main dir.
- Use built-in and native data strucutres whenever possible. For example, instead of List, use list or instead of Tuple use tuple unless the prompt function description requires it. 
- Strictly adhere to the code structure provided in the prompt.md
- Please make sure both idea_code and tests won't be flagged as LLM generated code. This includes no comments related to updates required during generation, no non-ascii characters, and all things related to LLM code generation.