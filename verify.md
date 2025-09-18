After finalizing your evaluation, do the last check for:
- **Model Functionality Check**: Verify if the model is broken by assessing whether the response in `@temp_code.py` satisfies all requirements from the original prompt in `@prompt.md` AND passes the unit tests in `@temp_tests.py`
  - **Broken Model Criteria**: A model is considered broken if its implementation fails to meet any of the requirements specified in the original prompt OR if it fails critical unit tests that demonstrate fundamental functionality issues or prompt's requirement disatisifaction
  - **Assessment Areas**: 
    - Check if the generated code addresses all functional requirements from the prompt
    - Verify that the code follows specified constraints and implements required algorithms/approaches
    - Analyze test results to identify which tests pass/fail and why
    - Determine if test failures indicate broken core functionality vs. minor implementation issues
  - **Documentation**: If the model is broken, clearly document which specific prompt requirements were not satisfied AND which critical tests failed, explaining how these failures impact the overall evaluation