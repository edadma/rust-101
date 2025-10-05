# Exercise 3: Palindrome Checker - Solution

## Simple Solution (with allocation)

```rust
pub fn is_palindrome(s: &str) -> bool {
    let cleaned: String = s.chars()
        .filter(|c| c.is_alphanumeric())
        .flat_map(|c| c.to_lowercase())
        .collect();

    let reversed: String = cleaned.chars().rev().collect();
    cleaned == reversed
}
```

## Optimized (single allocation)

```rust
pub fn is_palindrome(s: &str) -> bool {
    let chars: Vec<char> = s.chars()
        .filter(|c| c.is_alphanumeric())
        .flat_map(|c| c.to_lowercase())
        .collect();

    chars.iter().eq(chars.iter().rev())
}
```

## Alternative: Two-pointer approach

```rust
pub fn is_palindrome(s: &str) -> bool {
    let chars: Vec<char> = s.chars()
        .filter(|c| c.is_alphanumeric())
        .flat_map(|c| c.to_lowercase())
        .collect();

    let (mut left, mut right) = (0, chars.len().saturating_sub(1));

    while left < right {
        if chars[left] != chars[right] {
            return false;
        }
        left += 1;
        right -= 1;
    }

    true
}
```

## Explanation

**Key points:**
1. **chars() vs bytes()**: Use `chars()` for Unicode-aware iteration
2. **filter()**: Keeps only alphanumeric characters
3. **flat_map()**: `to_lowercase()` returns an iterator, `flat_map()` flattens it
4. **rev()**: Reverses an iterator
5. **eq()**: Compares two iterators element by element

**Why flat_map() instead of map()?**
- `to_lowercase()` returns an iterator because some characters expand when lowercased (e.g., German ß → ss)
- `flat_map()` flattens the nested iterators into a single stream

**Performance considerations:**
- First solution: 2 allocations (cleaned + reversed)
- Second solution: 1 allocation (chars Vec)
- Third solution: 1 allocation but manual iteration

The second solution is usually the best balance of clarity and performance.
