# Exercise 2: Sum of Squares - Hints

## Hint 1: Using a for loop

The simplest approach uses a for loop:
```rust
let mut sum = 0;
for &num in nums {
    sum += num * num;
}
sum
```

## Hint 2: Using iterator methods

You can use `map` to square each element, then `sum` to add them:
```rust
nums.iter().map(|&x| x * x).sum()
```

## Hint 3: Using fold

`fold` is a general accumulation method:
```rust
nums.iter().fold(0, |acc, &x| acc + x * x)
```
The first argument is the initial value, the closure takes (accumulator, element).
