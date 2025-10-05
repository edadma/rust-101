# Exercise 2: Sum of Squares

**Difficulty**: Beginner
**Concepts**: Vec basics, iteration, fold, closures

## Problem Statement

Write a function `sum_of_squares` that takes a slice of integers and returns the sum of their squares.

For example:
- `[1, 2, 3]` → 1² + 2² + 3² = 1 + 4 + 9 = 14
- `[2, 4]` → 2² + 4² = 4 + 16 = 20

## Learning Goals

- Work with slices (`&[T]`)
- Iterate over collections
- Use `fold` for accumulation
- Practice with closures
- Understand iterator methods

## Examples

```rust
assert_eq!(sum_of_squares(&[1, 2, 3]), 14);
assert_eq!(sum_of_squares(&[2, 4]), 20);
assert_eq!(sum_of_squares(&[]), 0);
```

## Starter Code

```rust
pub fn sum_of_squares(nums: &[i32]) -> i32 {
    // TODO: implement this function
    todo!()
}

#[cfg(test)]
mod tests {
    use super::*;

    #[test]
    fn test_basic() {
        assert_eq!(sum_of_squares(&[1, 2, 3]), 14);
    }

    #[test]
    fn test_two_elements() {
        assert_eq!(sum_of_squares(&[2, 4]), 20);
    }

    #[test]
    fn test_empty() {
        assert_eq!(sum_of_squares(&[]), 0);
    }

    #[test]
    fn test_single() {
        assert_eq!(sum_of_squares(&[5]), 25);
    }

    #[test]
    fn test_negative() {
        assert_eq!(sum_of_squares(&[-3, 4]), 25);
    }

    #[test]
    fn test_zeros() {
        assert_eq!(sum_of_squares(&[0, 0, 0]), 0);
    }
}
```

## Follow-up Challenges

1. Make it generic over any numeric type: `sum_of_squares<T>(nums: &[T]) -> T`
2. Implement `sum_of_cubes` using the same pattern
3. Create a generic `sum_of_powers(nums: &[i32], power: u32) -> i32`
4. Use `par_iter()` from rayon for parallel computation (research exercise)

## Key Takeaways

- `&[T]` is a slice - a view into a sequence of elements
- `iter()` creates an iterator over references to elements
- `map()` transforms each element
- `sum()` is a convenient method for numeric iterators
- `fold()` is the general accumulation pattern
- Closures `|x| ...` are anonymous functions
- Pattern `|&x|` destructures references in closure parameters


---

**Need help?** [View Hints](../../hints/02_sum_of_squares.html) | [View Solution](../../solutions/02_sum_of_squares.html)
