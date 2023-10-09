Template Litrals Explained in brief.

When you surround multiline text or any string with backticks  <code> ` </code> , it's called using a "template literal" or "template string." Template literals are a feature introduced in ECMAScript 2015 (ES6) and provide a more convenient way to work with strings in JavaScript, especially when you need to include variables or multiline text within a string.

Template literals offer a few advantages over traditional string concatenation or string interpolation methods:

1. **Multiline Text**: You can easily create multiline strings without needing to use newline characters (`\n`) or concatenation operators (`+`).

2. **Expression Interpolation**: You can embed expressions and variables directly within the string using `${}`. This allows you to inject dynamic values into the string without complex concatenation.

3. **Whitespace Preservation**: Template literals preserve whitespace, including leading whitespace, making them suitable for formatting code or text blocks.

Here's a basic example of a template literal:

```javascript
const name = "John";
const greeting = `Hello, ${name}!`;
```

In this example, `${name}` is an expression interpolation, and the resulting `greeting` string will contain "Hello, John!".

Using template literals is considered a more modern and readable way to work with strings in JavaScript, especially for tasks that involve generating HTML or other markup, constructing SQL queries, or building complex text content.
