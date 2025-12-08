🧹 Code Smells – Identification & Refactoring Reflections
⭐ What Are Code Smells?

Code smells are patterns in code that indicate deeper design or readability problems.
They don't stop the program from running, but they make future work harder.

🔥 1. Magic Numbers & Strings
❌ Smelly Code
function calculatePrice(quantity) {
  return quantity * 19.99; // Magic number
}

✅ Refactored Code
const PRICE_PER_ITEM = 19.99;

function calculatePrice(quantity) {
  return quantity * PRICE_PER_ITEM;
}

🔥 2. Long Functions
❌ Smelly Code
function processOrder(order) {
  console.log("Processing...");
  const total = order.items.reduce((sum, item) => sum + item.price, 0);

  if (total > 100) {
    console.log("Applying discount...");
    return total * 0.9;
  }

  return total;
}

✅ Refactored Code
function calculateTotal(items) {
  return items.reduce((sum, item) => sum + item.price, 0);
}

function applyDiscount(total) {
  return total > 100 ? total * 0.9 : total;
}

function processOrder(order) {
  console.log("Processing...");
  const total = calculateTotal(order.items);
  return applyDiscount(total);
}

🔥 3. Duplicate Code
❌ Smelly Code
let area1 = width * height;
let area2 = w * h;

✅ Refactored Code
function calculateArea(w, h) {
  return w * h;
}

let area1 = calculateArea(width, height);
let area2 = calculateArea(w, h);

🔥 4. Large Classes (God Objects)
❌ Smelly Code
class UserManager {
  createUser() {}
  deleteUser() {}
  sendEmail() {}
  logActivity() {}
  generateReport() {}
}

✅ Refactored Code
class UserService {
  createUser() {}
  deleteUser() {}
}

class EmailService {
  sendEmail() {}
}

class ActivityLogger {
  logActivity() {}
}

class ReportService {
  generateReport() {}
}

🔥 5. Deeply Nested Conditionals
❌ Smelly Code
if (user) {
  if (user.isActive) {
    if (user.role === "admin") {
      console.log("Access granted");
    }
  }
}

✅ Refactored Code
function canAccess(user) {
  if (!user) return false;
  if (!user.isActive) return false;
  return user.role === "admin";
}

if (canAccess(user)) {
  console.log("Access granted");
}

🔥 6. Commented-Out Code
❌ Smelly Code
// oldFunction();
// let x = 23;
let y = 10;

✅ Refactored Code
let y = 10;

🔥 7. Inconsistent Naming
❌ Smelly Code
let x = 10;
let Items = 20;
let item_count = 30;

✅ Refactored Code
let itemCount = 10;
let maxItems = 20;
let minItems = 30;

📝 Reflections
✔️ What code smells did I find?

Magic numbers

Long, overly complex functions

Duplicate code

God classes

Deep nested conditionals

Commented-out unused code

Inconsistent naming conventions

✔️ How did refactoring improve the code?

Refactoring made the code:

Easier to read

More modular and reusable

Less error-prone

Faster to debug

Cleaner for future developers

✔️ How does avoiding code smells make debugging easier?

Avoiding code smells:

Reduces confusion

Helps isolate bugs faster

Makes the code predictable

Improves collaboration

Prevents future technical debt
