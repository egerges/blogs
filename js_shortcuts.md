# 20 Underrated JavaScript Shortcuts for Fixing Common Development Issues (Part 2)

In part one, we explored some essential JavaScript shortcuts that improve code efficiency and readability. However, there are plenty of other shortcuts that, while less popular, can address daily development issues. In this blog, we dive deeper into 20 underrated JavaScript shortcuts that will help developers resolve common problems faster.

## 1. **Double Negation (`!!`) for Boolean Conversion**

When you need to convert a value to a boolean (true or false), using double negation is a concise way to do it.

### Before:
```javascript
const isActive = Boolean(user.isLoggedIn);
```

### After:
```javascript
const isActive = !!user.isLoggedIn;
```

This is particularly useful when handling truthy and falsy values, making it easier to convert them to a boolean.

## 2. **Array `filter(Boolean)` for Removing Falsy Values**

A quick way to clean an array from falsy values like `null`, `undefined`, `0`, `false`, and `""`.

### Before:
```javascript
const cleanArray = array.filter(item => item !== null && item !== undefined);
```

### After:
```javascript
const cleanArray = array.filter(Boolean);
```

This shortcut removes the need for verbose checks and makes the code cleaner.

## 3. **Array `fill()` for Populating Arrays**

Instead of using loops to populate an array with default values, the `fill()` method can do it in one line.

### Before:
```javascript
const arr = [];
for (let i = 0; i < 5; i++) {
  arr.push(0);
}
```

### After:
```javascript
const arr = new Array(5).fill(0);
```

This method is handy for creating arrays with pre-populated values.

## 4. **Object Freezing (`Object.freeze()`)**

To make objects immutable, you can use `Object.freeze()`. This prevents the modification of object properties, a simple fix for accidental data mutation issues.

### Example:
```javascript
const user = Object.freeze({ name: 'John', age: 30 });
// Attempting to modify user will fail silently (or throw in strict mode)
user.age = 40;
```

Freezing ensures your data remains unchanged throughout the program.

## 5. **Optional Callback Execution (`callback?.()`)**

Avoid checking if a callback function is passed or defined by using optional chaining with function calls.

### Before:
```javascript
if (typeof callback === 'function') {
  callback();
}
```

### After:
```javascript
callback?.();
```

This shortcut eliminates the need for a type check before invoking a callback.

## 6. **Array `some()` for Conditional Checking**

Instead of looping through an array to check if at least one element satisfies a condition, use `some()`.

### Before:
```javascript
let hasEven = false;
for (let i = 0; i < numbers.length; i++) {
  if (numbers[i] % 2 === 0) {
    hasEven = true;
    break;
  }
}
```

### After:
```javascript
const hasEven = numbers.some(num => num % 2 === 0);
```

This method is more readable and avoids manually managing loop breaks.

## 7. **Array `every()` for All-True Checking**

Similarly, `every()` checks if all elements in an array pass a test.

### Before:
```javascript
let allEven = true;
for (let i = 0; i < numbers.length; i++) {
  if (numbers[i] % 2 !== 0) {
    allEven = false;
    break;
  }
}
```

### After:
```javascript
const allEven = numbers.every(num => num % 2 === 0);
```

This cleans up the code and makes intent clearer.

## 8. **Dynamic Object Keys (`[]`)**

When dynamically assigning object keys, instead of creating a variable first, you can use bracket notation within the object.

### Before:
```javascript
const key = 'name';
const user = {};
user[key] = 'John';
```

### After:
```javascript
const user = { [key]: 'John' };
```

This is a cleaner and more concise way of assigning dynamic keys to objects.

## 9. **Exponentiation Operator (`**`)**

The exponentiation operator provides a shorter way to raise a number to a power.

### Before:
```javascript
const squared = Math.pow(3, 2);
```

### After:
```javascript
const squared = 3 ** 2;
```

This operator saves you from writing out the more verbose `Math.pow()` method.

## 10. **Array `flat()` for Flattening Arrays**

To flatten nested arrays without a custom function, use `flat()`.

### Before:
```javascript
const flattened = [].concat.apply([], nestedArray);
```

### After:
```javascript
const flattened = nestedArray.flat();
```

The `flat()` method is simple and readable, especially for multi-level arrays.

## 11. **Default Object Properties with Destructuring**

You can set default values for object properties directly when destructuring.

### Before:
```javascript
const name = user.name ? user.name : 'Anonymous';
const age = user.age ? user.age : 30;
```

### After:
```javascript
const { name = 'Anonymous', age = 30 } = user;
```

This method avoids repetitive ternary checks.

## 12. **Array `reduce()` for Summing Values**

Using `reduce()` is a concise way to perform aggregations like summing values in an array.

### Before:
```javascript
let sum = 0;
for (let i = 0; i < numbers.length; i++) {
  sum += numbers[i];
}
```

### After:
```javascript
const sum = numbers.reduce((acc, curr) => acc + curr, 0);
```

The `reduce()` method simplifies accumulation logic in arrays.

## 13. **Defaulting to an Empty Array (`|| []`)**

When working with arrays, you can avoid `undefined` or `null` errors by defaulting to an empty array.

### Before:
```javascript
const data = user.orders ? user.orders : [];
```

### After:
```javascript
const data = user.orders || [];
```

This ensures your variable always has an array, eliminating additional checks.

## 14. **`Number.isNaN()` to Avoid Pitfalls**

Avoid the confusion of `isNaN()`, which can return unexpected results due to type coercion.

### Before:
```javascript
isNaN('text'); // true
```

### After:
```javascript
Number.isNaN('text'); // false
```

This provides a more reliable check for `NaN`.

## 15. **Chaining `slice()` and `join()`**

To remove specific elements from an array and return a string, combine `slice()` and `join()`.

### Before:
```javascript
const arr = ['apple', 'banana', 'cherry'];
arr.splice(1, 1);
const str = arr.join(', ');
```

### After:
```javascript
const str = arr.slice(0, 1).concat(arr.slice(2)).join(', ');
```

This method avoids mutating the original array.

## 16. **String Padding (`padStart()` and `padEnd()`)**

To ensure consistent string lengths, use `padStart()` and `padEnd()`.

### Before:
```javascript
const str = '5';
while (str.length < 3) str = '0' + str;
```

### After:
```javascript
const str = '5'.padStart(3, '0');
```

This provides a cleaner and more efficient way to pad strings.

## 17. **Object Destructuring in Function Parameters**

Instead of extracting values from an object within a function body, you can destructure directly in the parameter list.

### Before:
```javascript
function displayUser(user) {
  const { name, age } = user;
  console.log(name, age);
}
```

### After:
```javascript
function displayUser({ name, age }) {
  console.log(name, age);
}
```

This makes your function signature more declarative.

## 18. **Shorthand for Math Functions (`+=`, `-=`, etc.)**

Instead of repeating variable names in math operations, use shorthand operators.

### Before:
```javascript
let count = 0;
count = count + 5;
```

### After:
```javascript
let count = 0;
count += 5;
```

This reduces verbosity in common mathematical operations.

## 19. **Combining Spread and Rest Operators**

You can use spread and rest operators together to extract parts of an object or array.

### Before:
```javascript
const { name, age, ...rest } = user;
console.log(rest);
```

### After:
```javascript
const user = { name: 'John', age: 30, location: 'Toronto' };
const { name, ...details } = user;
console.log(details);
```

This is useful for removing or extracting specific fields from an object.

## 20. **`new Set()` for Unique Values**

Using `new Set()` is an easy way to get unique values from an array.

### Before:
```javascript
const unique = array.filter((value, index, self) => self.indexOf(value) === index);
```

### After:
```javascript
const unique = [...new Set(array)];
```

This removes duplicates in a cleaner and more efficient way.

---

## Conclusion

These 20 underrated shortcuts will make your JavaScript code not only more concise but also more performant and readable. By mastering these less commonly discussed tricks, you
