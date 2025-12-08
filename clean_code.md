# Clean Code – Unit Testing Reflections

## ⭐ Why are unit tests important?
Unit tests help ensure each part of the code works as expected.  
They make the codebase more reliable by catching bugs early and preventing broken changes from being merged.  
Unit tests also:
- Encourage writing smaller, cleaner functions  
- Reduce fear when editing or refactoring code  
- Improve code readability and maintainability  
- Help detect errors immediately after changes are made  

## ⭐ How do unit tests keep code clean?
- By forcing clear inputs and outputs  
- By highlighting unnecessary complexity  
- By ensuring functions follow a single responsibility  
- By preventing regressions when adding new features  

## ⭐ Issues I found while testing
While running the tests, I encountered a module import error:

Cannot find module './math'


This helped me realize:
- My file name and import path didn’t match  
- Jest correctly pointed out the faulty line  
- After fixing the filename/path, the test passed  

This demonstrated how tests catch mistakes quickly and help improve code quality.

## ⭐ Final Thoughts
Writing unit tests made my code cleaner and more structured.  
It also gave me confidence that my function works correctly and will continue to work even after future changes.
