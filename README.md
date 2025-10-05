# Rust 101

A comprehensive collection of 101 Rust exercises designed to take you from beginner to confident Rustacean.

**Live Site:** https://edadma.github.io/rust-101/

## What is this?

Unlike micro-exercises like Rustlings, these exercises are substantial, practical problems that teach Rust concepts in context. Each exercise builds something real and satisfying.

## Prerequisites

- Basic programming experience (any language)
- Read through Chapter 9 of [The Rust Book](https://doc.rust-lang.org/book/)
- Rust installed (`rustup` recommended)

## Structure

The 101 exercises are organized into 10 phases:

1. **Foundations** (1-15): Basic syntax, ownership, simple collections
2. **Intermediate Collections** (16-30): Advanced collection usage
3. **Error Handling & I/O** (31-40): Result, Option, file operations
4. **Ownership Deep Dive** (41-50): Lifetimes, borrowing, Cow
5. **Smart Pointers** (51-65): Box, Rc, RefCell, Arc, Weak
6. **Trait System** (66-75): Traits, generics, trait objects
7. **Advanced Patterns** (76-85): Custom iterators, builder pattern
8. **Concurrency** (86-92): Threads, channels, sync primitives
9. **Real-World Algorithms** (93-100): Graph algorithms, DP, search
10. **Capstone** (101): Complete compiler + VM with event loop

## How to Work Through These Exercises

1. Visit the [live site](https://edadma.github.io/rust-101/)
2. Create a new Rust project for your solutions: `cargo new rust-101-solutions`
3. For each exercise, copy the starter code and tests
4. Implement the solution
5. Run tests with `cargo test`
6. Check hints if stuck, compare with solutions when done

## Repository Contents

- `book/` - mdBook source files for the website
- `curriculum.md` - Complete list of all 101 exercises with descriptions
- `problem_ideas.md` - Brainstorm of additional exercise ideas
- `language_grammar.md` - Grammar for the capstone compiler project

## Contributing

This is a personal learning project. Feel free to fork and adapt for your own learning!

## Building the Book Locally

```bash
# Install mdBook
cargo install mdbook

# Build and serve locally
cd book
mdbook serve --open
```

## License

MIT
