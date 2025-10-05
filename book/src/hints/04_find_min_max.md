# Exercise 4: Find Min/Max - Hints

## Hint 1: Using iterator methods

The simplest approach uses iterator methods:
```rust
pub fn find_min(nums: &[i32]) -> Option<i32> {
    nums.iter().min().copied()
}
```

The `min()` method returns `Option<&i32>`, so use `.copied()` to convert to `Option<i32>`.

## Hint 2: Handling empty slices

Iterator methods like `min()` and `max()` automatically return `None` for empty iterators:
```rust
let empty: &[i32] = &[];
assert_eq!(empty.iter().min(), None);
```

## Hint 3: Manual implementation with fold

You can use `fold` to find min/max manually:
```rust
pub fn find_min(nums: &[i32]) -> Option<i32> {
    if nums.is_empty() {
        return None;
    }

    Some(nums.iter().fold(nums[0], |min, &x| {
        if x < min { x } else { min }
    }))
}
```

## Hint 4: Finding both min and max

For `find_min_max`, you need to track both values in a single pass:
```rust
pub fn find_min_max(nums: &[i32]) -> Option<(i32, i32)> {
    if nums.is_empty() {
        return None;
    }

    let first = nums[0];
    let (min, max) = nums.iter().fold((first, first), |(min, max), &x| {
        (min.min(x), max.max(x))
    });

    Some((min, max))
}
```

## Hint 5: Pattern matching on Option

When using the result, pattern match to handle both cases:
```rust
match find_min(&numbers) {
    Some(min) => println!("Minimum: {}", min),
    None => println!("Empty slice"),
}
```
