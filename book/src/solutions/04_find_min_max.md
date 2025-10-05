# Exercise 4: Find Min/Max - Solution

## Idiomatic Solution (using iterator methods)

```rust
pub fn find_min(nums: &[i32]) -> Option<i32> {
    nums.iter().min().copied()
}

pub fn find_max(nums: &[i32]) -> Option<i32> {
    nums.iter().max().copied()
}

pub fn find_min_max(nums: &[i32]) -> Option<(i32, i32)> {
    if nums.is_empty() {
        return None;
    }

    let min = nums.iter().min().copied().unwrap();
    let max = nums.iter().max().copied().unwrap();
    Some((min, max))
}
```

## Alternative: Single-pass min_max

```rust
pub fn find_min_max(nums: &[i32]) -> Option<(i32, i32)> {
    if nums.is_empty() {
        return None;
    }

    let first = nums[0];
    let (min, max) = nums.iter().skip(1).fold((first, first), |(min, max), &x| {
        (min.min(x), max.max(x))
    });

    Some((min, max))
}
```

## Alternative: Using fold

```rust
pub fn find_min(nums: &[i32]) -> Option<i32> {
    nums.first().map(|&first| {
        nums.iter().skip(1).fold(first, |min, &x| min.min(x))
    })
}

pub fn find_max(nums: &[i32]) -> Option<i32> {
    nums.first().map(|&first| {
        nums.iter().skip(1).fold(first, |max, &x| max.max(x))
    })
}
```

## Alternative: Manual loop

```rust
pub fn find_min(nums: &[i32]) -> Option<i32> {
    if nums.is_empty() {
        return None;
    }

    let mut min = nums[0];
    for &num in &nums[1..] {
        if num < min {
            min = num;
        }
    }
    Some(min)
}

pub fn find_max(nums: &[i32]) -> Option<i32> {
    if nums.is_empty() {
        return None;
    }

    let mut max = nums[0];
    for &num in &nums[1..] {
        if num > max {
            max = num;
        }
    }
    Some(max)
}

pub fn find_min_max(nums: &[i32]) -> Option<(i32, i32)> {
    if nums.is_empty() {
        return None;
    }

    let mut min = nums[0];
    let mut max = nums[0];

    for &num in &nums[1..] {
        if num < min {
            min = num;
        }
        if num > max {
            max = num;
        }
    }

    Some((min, max))
}
```

## Explanation

**Key points:**

1. **Iterator methods**: `min()` and `max()` return `Option<&i32>`
   - Use `.copied()` or `.cloned()` to convert to `Option<i32>`

2. **Why Option?**: Empty slices have no min/max value
   - Better than panicking or returning sentinel values like `-1`
   - Forces the caller to handle the empty case

3. **Single-pass algorithm**: For `find_min_max`, we can find both in one iteration
   - Start with `first` as both min and max
   - Update both as we iterate
   - More efficient than calling `min()` and `max()` separately

4. **Using .first()**: Returns `Option<&i32>` for the first element
   - Safe way to check if slice is non-empty
   - Can chain with `.map()` for elegant Option handling

5. **Pattern matching**: Not shown in solutions, but usage would be:
   ```rust
   if let Some(min) = find_min(&nums) {
       println!("Minimum: {}", min);
   }
   ```

**Performance note:**
The idiomatic `find_min_max` solution makes two passes (one for min, one for max). The single-pass version with `fold` is more efficient but slightly less clear.
