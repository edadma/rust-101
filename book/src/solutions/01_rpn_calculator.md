# Exercise 1: RPN Calculator - Solution

## Main Solution

```rust
pub fn rpn_calc(expr: &str) -> Result<i32, String> {
    let mut stack: Vec<i32> = Vec::new();

    for token in expr.split_whitespace() {
        match token {
            "+" => {
                let b = stack.pop().ok_or("Stack underflow")?;
                let a = stack.pop().ok_or("Stack underflow")?;
                stack.push(a + b);
            }
            "-" => {
                let b = stack.pop().ok_or("Stack underflow")?;
                let a = stack.pop().ok_or("Stack underflow")?;
                stack.push(a - b);
            }
            "*" => {
                let b = stack.pop().ok_or("Stack underflow")?;
                let a = stack.pop().ok_or("Stack underflow")?;
                stack.push(a * b);
            }
            "/" => {
                let b = stack.pop().ok_or("Stack underflow")?;
                let a = stack.pop().ok_or("Stack underflow")?;
                if b == 0 {
                    return Err("Division by zero".to_string());
                }
                stack.push(a / b);
            }
            _ => {
                // Try to parse as number
                let num = token
                    .parse::<i32>()
                    .map_err(|_| format!("Invalid token: {}", token))?;
                stack.push(num);
            }
        }
    }

    // Should have exactly one value left
    if stack.len() == 1 {
        Ok(stack[0])
    } else if stack.is_empty() {
        Err("Empty expression".to_string())
    } else {
        Err(format!("Too many operands: {} left on stack", stack.len()))
    }
}
```

## Alternative Solution: With Helper Function

```rust
pub fn rpn_calc(expr: &str) -> Result<i32, String> {
    let mut stack: Vec<i32> = Vec::new();

    fn apply_op(stack: &mut Vec<i32>, op: fn(i32, i32) -> Result<i32, String>) -> Result<(), String> {
        let b = stack.pop().ok_or("Stack underflow")?;
        let a = stack.pop().ok_or("Stack underflow")?;
        stack.push(op(a, b)?);
        Ok(())
    }

    for token in expr.split_whitespace() {
        match token {
            "+" => apply_op(&mut stack, |a, b| Ok(a + b))?,
            "-" => apply_op(&mut stack, |a, b| Ok(a - b))?,
            "*" => apply_op(&mut stack, |a, b| Ok(a * b))?,
            "/" => apply_op(&mut stack, |a, b| {
                if b == 0 {
                    Err("Division by zero".to_string())
                } else {
                    Ok(a / b)
                }
            })?,
            _ => stack.push(token.parse().map_err(|_| format!("Invalid token: {}", token))?),
        }
    }

    match stack.len() {
        0 => Err("Empty expression".to_string()),
        1 => Ok(stack[0]),
        _ => Err(format!("Too many operands: {} left on stack", stack.len())),
    }
}
```

## Explanation

**Key points:**
1. **Vec as stack**: We use `Vec::push()` and `Vec::pop()` for stack operations
2. **Result propagation**: The `?` operator propagates errors early
3. **Option to Result**: `ok_or()` converts `Option<T>` from `pop()` to `Result<T, E>`
4. **Parse with error mapping**: `parse()` returns `Result`, we use `map_err()` to customize the error message
5. **Order matters**: When popping for operators like `-` and `/`, we pop `b` first, then `a`
6. **Final validation**: We ensure exactly one value remains on the stack

**Common mistakes to avoid:**
- Forgetting to check for division by zero
- Wrong order when popping operands (leads to reversed subtraction/division)
- Not validating final stack size
- Not handling empty input
