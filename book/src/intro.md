# Introduction

Welcome to **Rust 101** - a comprehensive collection of 101 exercises designed to take you from Rust beginner to confident Rustacean.

## What Makes This Different?

Unlike micro-exercises like Rustlings, these exercises are:
- **Substantial**: Each exercise builds something real and satisfying
- **Progressive**: Concepts build naturally on each other
- **Comprehensive**: Forces you to use every Rust feature in context
- **Practical**: Skills transfer directly to real-world Rust programming

## Structure

The 101 exercises are organized into 10 phases:

1. **Foundations** (1-15): Basic syntax, ownership, simple collections
2. **Intermediate Collections** (16-30): Advanced collection usage, patterns
3. **Error Handling & I/O** (31-40): Result, Option, file operations
4. **Ownership Deep Dive** (41-50): Lifetimes, borrowing, Cow
5. **Smart Pointers** (51-65): Box, Rc, RefCell, Arc, Weak
6. **Trait System** (66-75): Traits, generics, trait objects
7. **Advanced Patterns** (76-85): Custom iterators, builder pattern, typestate
8. **Concurrency** (86-92): Threads, channels, sync primitives
9. **Real-World Algorithms** (93-100): Graph algorithms, DP, search
10. **Capstone** (101): Complete compiler + VM with event loop

## How to Use This Book

1. **Read the exercise** - Understand what you're building
2. **Try it yourself** - Write code without looking at hints
3. **Run the tests** - Use `cargo test` to validate your solution
4. **Peek at hints** - If stuck, hints are in a separate section
5. **Compare solutions** - After solving, see alternative approaches
6. **Do follow-ups** - Extend the exercise with additional challenges

## Prerequisites

- Basic programming experience (any language)
- Rust installed (`rustup` recommended)
- Familiarity with command line
- A code editor (VS Code, RustRover, etc.)

## Philosophy

These exercises teach Rust by:
- **Forcing natural usage**: You'll reach for `Rc<RefCell<T>>` because you need it, not because you memorized when to use it
- **Building intuition**: Patterns emerge from solving real problems
- **Embracing difficulty**: Ownership errors teach better than explanations
- **Celebrating progress**: Each solved exercise is a real achievement

Ready to start? Head to [Exercise 1: RPN Calculator](./phase1/01_rpn_calculator.md)!
