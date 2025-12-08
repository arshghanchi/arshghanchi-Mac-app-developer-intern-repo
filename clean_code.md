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

## 📝 Commenting & Documentation Reflections

### ⭐ When should you add comments?
Comments should be added when:
- The *reasoning* behind code is not obvious  
- The logic is complex and cannot be simplified  
- You need to explain *why* something is done, not just what it does  
- There are special cases, assumptions, or limitations future developers must know  
- A function or module is part of a public API and benefits from documentation  

---

### 🛑 When should you avoid comments and improve the code instead?
Avoid comments when:
- The comment repeats what the code already says  
  - Example: `i = i + 1; // increments i`  
- You can make the code clearer by renaming variables or functions  
- The code can be refactored to be self-explanatory  
- Comments are being used to explain messy code instead of fixing it  
- The code could be simplified enough that the comment becomes unnecessary  

---

### ❌ Example of poorly commented code
```js
// add numbers
function a(x, y) {
  // sum
  return x + y; // return
}
✔️ Improved version with proper documentation

/**
 * Adds two numbers and returns the result.
 * @param {number} x - The first number
 * @param {number} y - The second number
 * @returns {number} The sum of x and y
 */
function add(x, y) {
  return x + y;
}

💡 What I learned

Good comments explain the intent, not the obvious code behavior

Clean, readable code reduces the need for comments

Documentation helps others understand design decisions and assumptions

If a comment feels necessary to understand simple code, the code should be improved instead

# 🧹 Refactoring Code for Simplicity – Reflections
## ⭐ What Makes Code Overly Complex?

Code often becomes unnecessarily complex when:

It has too many unnecessary steps

It tries to handle multiple responsibilities in one place

It includes deeply nested conditionals that obscure the logic

It introduces abstractions (extra classes/functions) that do not add value

It is technically correct but difficult to read or maintain

It repeats logic or does extra work for simple tasks

## 💀 Example of Overly Complicated Code (Before Refactoring)
// Over-engineered function to check if a user is an adult
function isAdult(user) {
    if (user !== null && user !== undefined) {
        if (typeof user.age === "number") {
            if (user.age > 0) {
                if (user.age >= 18) {
                    return true;
                } else {
                    return false;
                }
            } else {
                return false;
            }
        } else {
            return false;
        }
    } else {
        return false;
    }
}

## ❌ Problems Identified

Too many nested if conditions

Multiple return false statements

Hard to read and maintain

Performs more checks than needed

Intent is buried under layers of logic

## ✅ Refactored Simpler Version
function isAdult(user) {
    if (!user || typeof user.age !== "number" || user.age <= 0) return false;
    return user.age >= 18;
}

## ✔️ Improvements After Refactoring

Reduced 12 lines → 2 lines

Logic is simple, direct, and easy to follow

All original functionality preserved

Clear validation in a single conditional

Easier to debug and extend later

## 📝 Reflections
### 🔍 What Made the Original Code Complex?

Too many nested conditionals

Repeated validation logic

No concise or combined checks

Difficult to understand at a glance

Intent was not immediately visible

### ✨ How Refactoring Improved the Code

Simplified logic using early returns

Removed redundant checks

Improved readability and structure

Only one clear path for invalid data

The purpose (“Is the user an adult?”) is immediately obvious


