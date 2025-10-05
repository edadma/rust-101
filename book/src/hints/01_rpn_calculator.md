# Exercise 1: RPN Calculator - Hints

## Hint 1: Algorithm overview

RPN uses a stack:
1. Split input by whitespace
2. For each token:
   - If it's a number, push it onto the stack
   - If it's an operator, pop two operands, apply operator, push result
3. At the end, stack should have exactly one value

```rust
let mut stack: Vec<i32> = Vec::new();
```

## Hint 2: Splitting the input

Use `split_whitespace()` to tokenize:
```rust
for token in expr.split_whitespace() {
    // process token
}
```

## Hint 3: Parsing numbers

Use `parse()` with error handling:
```rust
if let Ok(num) = token.parse::<i32>() {
    stack.push(num);
}
```

## Hint 4: Handling operators

Match on the operator and pop two values:
```rust
match token {
    "+" => {
        let b = stack.pop().ok_or("Stack underflow")?;
        let a = stack.pop().ok_or("Stack underflow")?;
        stack.push(a + b);
    }
    // ... other operators
}
```

Note: Order matters! For `a - b`, you pop `b` first, then `a`.

## Hint 5: Final validation

After processing all tokens, check the stack:
```rust
if stack.len() == 1 {
    Ok(stack[0])
} else if stack.is_empty() {
    Err("Empty expression".to_string())
} else {
    Err("Too many operands".to_string())
}
```
