# Exercise 4: Find Min/Max

**Difficulty:** Beginner
**Concepts:** Option, pattern matching, slice iteration, multiple return values

## Exercise Statement

Write two functions that find the minimum and maximum values in a slice of integers.

**Key learning points:**
- Return `Option<i32>` to handle empty slices
- Use pattern matching to handle the `Option` type
- Understand when to use `Option` vs panicking
- Practice with slice iteration

## Learning Goals

- Understand `Option<T>` and when to use it
- Pattern match on `Option` with `Some` and `None`
- Handle edge cases (empty slices)
- Use `min()` and `max()` methods on iterators
- Return multiple values using tuples

## Examples

```rust
assert_eq!(find_min(&[3, 1, 4, 1, 5]), Some(1));
assert_eq!(find_max(&[3, 1, 4, 1, 5]), Some(5));
assert_eq!(find_min(&[]), None);
assert_eq!(find_max(&[]), None);

// Bonus: find both at once
assert_eq!(find_min_max(&[3, 1, 4, 1, 5]), Some((1, 5)));
assert_eq!(find_min_max(&[]), None);
```

## Starter Code

```rust
pub fn find_min(nums: &[i32]) -> Option<i32> {
    // TODO: implement this function
    todo!()
}

pub fn find_max(nums: &[i32]) -> Option<i32> {
    // TODO: implement this function
    todo!()
}

// Bonus: return both min and max in a single pass
pub fn find_min_max(nums: &[i32]) -> Option<(i32, i32)> {
    // TODO: implement this function
    todo!()
}

#[cfg(test)]
mod tests {
    use super::*;

    #[test]
    fn test_find_min_basic() {
        assert_eq!(find_min(&[3, 1, 4, 1, 5]), Some(1));
    }

    #[test]
    fn test_find_min_single() {
        assert_eq!(find_min(&[42]), Some(42));
    }

    #[test]
    fn test_find_min_empty() {
        assert_eq!(find_min(&[]), None);
    }

    #[test]
    fn test_find_min_negative() {
        assert_eq!(find_min(&[-5, -1, -10, -3]), Some(-10));
    }

    #[test]
    fn test_find_max_basic() {
        assert_eq!(find_max(&[3, 1, 4, 1, 5]), Some(5));
    }

    #[test]
    fn test_find_max_single() {
        assert_eq!(find_max(&[42]), Some(42));
    }

    #[test]
    fn test_find_max_empty() {
        assert_eq!(find_max(&[]), None);
    }

    #[test]
    fn test_find_max_negative() {
        assert_eq!(find_max(&[-5, -1, -10, -3]), Some(-1));
    }

    #[test]
    fn test_find_min_max_basic() {
        assert_eq!(find_min_max(&[3, 1, 4, 1, 5]), Some((1, 5)));
    }

    #[test]
    fn test_find_min_max_single() {
        assert_eq!(find_min_max(&[42]), Some((42, 42)));
    }

    #[test]
    fn test_find_min_max_empty() {
        assert_eq!(find_min_max(&[]), None);
    }

    #[test]
    fn test_find_min_max_all_same() {
        assert_eq!(find_min_max(&[7, 7, 7, 7]), Some((7, 7)));
    }
}
```

## Follow-up Challenges

1. Make the functions generic over any type that implements `Ord`
2. Implement using only a `for` loop (no iterator methods)
3. Find the index of the min/max value instead of the value itself
4. Return both the value and its index: `Option<(i32, usize)>`
5. Handle `f64` slices (think about `NaN` and `Infinity`)

## Key Takeaways

- `Option<T>` represents a value that might not exist
- `Some(value)` contains a value, `None` represents absence
- Use `Option` instead of panicking or returning sentinel values (-1, null, etc.)
- Iterator methods like `min()` and `max()` return `Option`
- Tuples `(T, U)` are useful for returning multiple values
- Pattern matching is the idiomatic way to unwrap `Option` values
- Empty slices are a natural use case for `Option::None`

---

**Need help?** [View Hints](../../hints/04_find_min_max.html) | [View Solution](../../solutions/04_find_min_max.html)
