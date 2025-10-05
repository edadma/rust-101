# Exercise 3: Palindrome Checker - Hints

## Hint 1: Cleaning the string

First, filter to keep only alphanumeric characters and convert to lowercase:
```rust
let cleaned: String = s.chars()
    .filter(|c| c.is_alphanumeric())
    .flat_map(|c| c.to_lowercase())
    .collect();
```

## Hint 2: Comparing forward and backward

Once cleaned, compare the string with its reverse:
```rust
let reversed: String = cleaned.chars().rev().collect();
cleaned == reversed
```

## Hint 3: More efficient approach

For a solution with single allocation:
```rust
let chars: Vec<char> = s.chars()
    .filter(|c| c.is_alphanumeric())
    .flat_map(|c| c.to_lowercase())
    .collect();

chars.iter().eq(chars.iter().rev())
```

## Hint 4: Why chars() not bytes()?

Use `chars()` instead of `bytes()` to handle Unicode correctly:
- `"café".bytes()` → 5 bytes (é is multi-byte)
- `"café".chars()` → 4 characters
