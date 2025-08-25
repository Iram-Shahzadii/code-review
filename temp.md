❌ Bad Code:
```javascript
function sum(){ return a+b;}
```

🔍 Issues:
• ❌ **Global Variable Reliance:** The function implicitly relies on global variables `a` and `b`. This makes the
function's behavior unpredictable as it depends on external state that isn't explicitly passed in, leading to tightly
coupled code.
• ❌ **Lack of Parameters:** Functions should ideally operate on explicit inputs passed as parameters. Without them, it's
unclear what values `a` and `b` are supposed to represent or where they come from.
• ❌ **Potential Runtime Errors:** If `a` or `b` are not defined in the global scope when `sum()` is called, it will
result in a `ReferenceError`. If they are defined but not numbers, it could lead to unexpected type coercion (e.g.,
string concatenation) or `NaN`.
• ❌ **Poor Readability & Maintainability:** The function's purpose and expected inputs are not immediately obvious,
making it harder to understand, debug, and reuse.
• ❌ **No Documentation:** Missing comments or JSDoc to explain its purpose, parameters, and return value.

✅ Recommended Fix:
```javascript
/**
* Calculates the sum of two numbers.
* @param {number} num1 - The first number to sum.
* @param {number} num2 - The second number to sum.
* @returns {number} The sum of num1 and num2.
* @throws {TypeError} If either num1 or num2 is not a number.
*/
function sum(num1, num2) {
if (typeof num1 !== 'number' || typeof num2 !== 'number') {
throw new TypeError("Both arguments for 'sum' must be numbers.");
}
return num1 + num2;
}

// Example usage:
// console.log(sum(5, 3)); // Output: 8
// console.log(sum(10, -2)); // Output: 8
// try {
// sum("hello", 3);
// } catch (e) {
// console.error(e.message); // Output: Both arguments for 'sum' must be numbers.
// }
```

💡 Improvements:
• ✔ **Explicit Parameters:** The function now clearly defines `num1` and `num2` as its inputs, making it self-contained
and easy to understand.
• ✔ **Increased Reliability & Predictability:** The function's behavior is now predictable and independent of the global
scope.
• ✔ **Basic Type Validation:** Added a check to ensure inputs are numbers, preventing common type-related bugs and
providing clearer error messages.
• ✔ **Enhanced Readability & Reusability:** The function is now much easier to read, use, and reuse in different parts
of your application.
• ✔ **Proper Documentation:** Includes JSDoc comments to clearly describe its purpose, parameters, and return type,
which is crucial for maintainability.