# Exercise 2: Sum of Squares - Solution

## Idiomatic Solution (using map + sum)

```rust
pub fn sum_of_squares(nums: &[i32]) -> i32 {
    nums.iter().map(|&x| x * x).sum()
}
```

## Alternative: Using fold

```rust
pub fn sum_of_squares(nums: &[i32]) -> i32 {
    nums.iter().fold(0, |acc, &x| acc + x * x)
}
```

## Alternative: Using for loop (more explicit)

```rust
pub fn sum_of_squares(nums: &[i32]) -> i32 {
    let mut sum = 0;
    for &num in nums {
        sum += num * num;
    }
    sum
}
```

## Explanation

**Key points:**
1. **Slices**: `&[i32]` is a borrowed view into a sequence of integers
2. **Iterator methods**: `iter()`, `map()`, and `sum()` chain together for clean, functional code
3. **Closures**: `|&x| x * x` is a closure that takes a reference and squares it
4. **Pattern destructuring**: `|&x|` destructures the reference, giving us the value directly
5. **Type inference**: `sum()` knows to return `i32` based on the context

**Why the idiomatic solution is preferred:**
- Concise and readable
- No mutable state
- Composable with other iterator methods
- Compiler can optimize well
- Handles empty slices automatically (returns 0)
