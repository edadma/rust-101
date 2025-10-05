# Exercise 1: RPN Calculator

**Difficulty:** Beginner
**Concepts:** String vs &str, Vec as stack, Result, pattern matching, parsing

## Problem Statement

Implement a simple Reverse Polish Notation (RPN) calculator that evaluates arithmetic expressions.

In RPN, operators come after operands:
- `3 4 +` means 3 + 4 = 7
- `5 1 2 + 4 * + 3 -` means (5 + ((1 + 2) * 4)) - 3 = 14

**Requirements:**
- Support operators: `+`, `-`, `*`, `/`
- Integer arithmetic only
- Division rounds toward zero (truncates)
- All tokens must be separated by whitespace
- Return `Result<i32, String>` for success or error
- Handle errors: invalid tokens, stack underflow, leftover values

**Optional (no tests provided, but try it!):**
- Support negative numbers (e.g., `-5 3 +` = -2)

## Learning Goals

- Understand `String` vs `&str`
- Use `Vec` as a stack (push/pop)
- Return `Result` for error handling
- Parse strings to numbers
- Pattern matching with `match`
- Split strings and iterate over tokens

## Examples

```rust
assert_eq!(rpn_calc("3 4 +"), Ok(7));
assert_eq!(rpn_calc("5 1 2 + 4 * + 3 -"), Ok(14));
assert_eq!(rpn_calc("10 3 /"), Ok(3));  // integer division
assert_eq!(rpn_calc(""), Err("Empty expression".to_string()));
assert!(rpn_calc("3 0 /").is_err());  // division by zero
assert!(rpn_calc("1 2 3 +").is_err());  // too many operands
```

## Starter Code

```rust
pub fn rpn_calc(expr: &str) -> Result<i32, String> {
    // TODO: implement this function
    todo!()
}

#[cfg(test)]
mod tests {
    use super::*;

    #[test]
    fn test_addition() {
        assert_eq!(rpn_calc("3 4 +"), Ok(7));
    }

    #[test]
    fn test_subtraction() {
        assert_eq!(rpn_calc("10 3 -"), Ok(7));
    }

    #[test]
    fn test_multiplication() {
        assert_eq!(rpn_calc("3 4 *"), Ok(12));
    }

    #[test]
    fn test_division() {
        assert_eq!(rpn_calc("10 3 /"), Ok(3));
        assert_eq!(rpn_calc("7 2 /"), Ok(3));
    }

    #[test]
    fn test_complex() {
        // 5 + ((1 + 2) * 4) - 3 = 14
        assert_eq!(rpn_calc("5 1 2 + 4 * + 3 -"), Ok(14));
    }

    #[test]
    fn test_single_number() {
        assert_eq!(rpn_calc("42"), Ok(42));
    }

    #[test]
    fn test_empty() {
        assert!(rpn_calc("").is_err());
    }

    #[test]
    fn test_division_by_zero() {
        assert!(rpn_calc("3 0 /").is_err());
    }

    #[test]
    fn test_too_many_operands() {
        assert!(rpn_calc("1 2 3 +").is_err());
    }

    #[test]
    fn test_insufficient_operands() {
        assert!(rpn_calc("1 +").is_err());
    }

    #[test]
    fn test_invalid_token() {
        assert!(rpn_calc("1 2 xyz").is_err());
    }
}
```

## Follow-up Challenges

1. Add support for negative numbers (e.g., "-5 3 +" = -2)
2. Add more operators: `%` (modulo), `**` (power)
3. Add stack operations: `dup` (duplicate top), `swap` (swap top two)
4. Convert infix expressions to RPN (requires parsing precedence)
5. Make it generic over any numeric type using traits

## Key Takeaways

- `&str` accepts both string literals and `&String` references
- `Vec` works perfectly as a stack with `push()` and `pop()`
- `pop()` returns `Option<T>` - use `ok_or()` to convert to `Result`
- `Result<T, E>` is Rust's way of handling errors
- `?` operator propagates errors early
- `parse::<T>()` converts strings to numbers
- `match` is powerful for pattern matching on strings
- `split_whitespace()` handles any amount of whitespace
- Order matters when popping from stack for non-commutative operators

---

**Need help?** [View Hints](/rust-101/hints/01_rpn_calculator.html) | [View Solution](/rust-101/solutions/01_rpn_calculator.html)
