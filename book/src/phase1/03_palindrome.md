# Exercise 3: Palindrome Checker

**Difficulty**: Beginner
**Concepts**: String iteration, chars vs bytes, reversal, borrowing

## Problem Statement

Write a function `is_palindrome` that checks if a string reads the same forwards and backwards.

Ignore case and non-alphanumeric characters. For example:
- `"racecar"` → true
- `"A man, a plan, a canal: Panama"` → true
- `"hello"` → false

## Learning Goals

- Iterate over characters with `.chars()`
- Understand the difference between chars and bytes
- Filter and transform characters
- Compare strings/iterators
- Handle Unicode properly

## Examples

```rust
assert_eq!(is_palindrome("racecar"), true);
assert_eq!(is_palindrome("hello"), false);
assert_eq!(is_palindrome("A man, a plan, a canal: Panama"), true);
assert_eq!(is_palindrome(""), true);
```

## Starter Code

```rust
pub fn is_palindrome(s: &str) -> bool {
    // TODO: implement this function
    todo!()
}

#[cfg(test)]
mod tests {
    use super::*;

    #[test]
    fn test_simple_palindrome() {
        assert_eq!(is_palindrome("racecar"), true);
    }

    #[test]
    fn test_not_palindrome() {
        assert_eq!(is_palindrome("hello"), false);
    }

    #[test]
    fn test_with_spaces_and_punctuation() {
        assert_eq!(is_palindrome("A man, a plan, a canal: Panama"), true);
    }

    #[test]
    fn test_empty() {
        assert_eq!(is_palindrome(""), true);
    }

    #[test]
    fn test_single_char() {
        assert_eq!(is_palindrome("a"), true);
    }

    #[test]
    fn test_mixed_case() {
        assert_eq!(is_palindrome("RaceCar"), true);
    }

    #[test]
    fn test_numbers() {
        assert_eq!(is_palindrome("12321"), true);
        assert_eq!(is_palindrome("12345"), false);
    }
}
```

## Follow-up Challenges

1. Implement without allocating any String or Vec
2. Make a case-sensitive version
3. Create a function that returns the longest palindromic substring
4. Handle grapheme clusters (combined Unicode characters) correctly using the `unicode-segmentation` crate

## Key Takeaways

- `chars()` iterates over Unicode scalar values (characters)
- `bytes()` iterates over raw bytes (not Unicode-aware)
- `filter()` keeps elements matching a predicate
- `flat_map()` is useful when a function returns an iterator (like `to_lowercase()`)
- `collect()` gathers iterator elements into a collection
- `rev()` reverses an iterator
- Always consider Unicode when working with text


---

**Need help?** [View Hints](/rust-101/hints/03_palindrome.html) | [View Solution](/rust-101/solutions/03_palindrome.html)
