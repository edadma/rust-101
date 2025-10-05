# Random Problem Ideas for Rust Learning

This is a braindump of potential problems. Not ordered, just capturing ideas.

## Text & String Processing
- [ ] Word frequency counter (HashMap<String, usize>)
- [ ] Anagram detector (grouping, HashSet)
- [ ] Text justification (Vec manipulation, String building)
- [ ] Markdown parser (enum for AST, pattern matching)
- [ ] Substring search with multiple algorithms (KMP, Boyer-Moore)
- [ ] UTF-8 character iterator (understanding chars vs bytes)
- [ ] String interning system (Rc<str>, HashMap)
- [ ] Trie implementation for autocomplete
- [ ] Regex-like pattern matcher (recursive structures, Box)
- [ ] CSV parser with custom error types
- [ ] ROT13/Caesar cipher (bytes, char manipulation)
- [ ] Palindrome checker with multiple approaches
- [ ] Longest common subsequence

## Collections Deep Dive
- [ ] LRU cache (HashMap + VecDeque or custom doubly-linked list)
- [ ] Priority queue scheduler (BinaryHeap)
- [ ] Circular buffer (VecDeque or custom)
- [ ] Bloom filter (BitVec-like structure)
- [ ] Skip list implementation
- [ ] Ring buffer for audio samples
- [ ] Fixed-size stack allocator (Box, unsafe)
- [ ] Memory pool allocator
- [ ] Sparse matrix (HashMap of coordinates)
- [ ] Interval tree (BTreeMap)
- [ ] Disjoint set (union-find) with path compression
- [ ] MultiMap implementation (HashMap<K, Vec<V>>)

## Graph & Tree Problems
- [ ] Graph representation (adjacency list with Vec<Vec<usize>> vs Rc/RefCell)
- [ ] Dijkstra's shortest path
- [ ] Topological sort
- [ ] Strongly connected components (Tarjan's)
- [ ] Binary tree with parent pointers (Weak pointers)
- [ ] N-ary tree with arbitrary children (Vec<Rc<RefCell<Node>>>)
- [ ] Graph cycle detection
- [ ] Minimum spanning tree (Kruskal's with union-find)
- [ ] A* pathfinding
- [ ] Binary search tree with balancing
- [ ] Trie for IP routing table
- [ ] Graph coloring problem
- [ ] Traveling salesman (backtracking with state)

## Simulations & Games
- [ ] Conway's Game of Life (2D Vec, borrowing patterns)
- [ ] Snake game state machine
- [ ] Particle physics simulation (Vec of particles, mutation)
- [ ] Poker hand evaluator (enums, Ord trait)
- [ ] Chess move validator (complex enums, pattern matching)
- [ ] Minesweeper generator and solver
- [ ] Tetris piece rotation and collision
- [ ] Dungeon generator (procedural, random)
- [ ] Elevator scheduling algorithm
- [ ] Traffic light controller (state machine)
- [ ] Inventory management system (trait objects for items)
- [ ] RPG character system with stats and effects

## Parsers & Interpreters
- [ ] JSON parser (enum for Value type, recursive structures)
- [ ] Lisp/Scheme interpreter (Rc for cons cells)
- [ ] Calculator with shunting yard algorithm
- [ ] Pratt parser for expressions
- [ ] INI file parser
- [ ] S-expression parser
- [ ] Bytecode VM with stack
- [ ] Query language parser (SQL-like)
- [ ] Command-line argument parser (custom, not clap)
- [ ] Regex engine (NFA/DFA)
- [ ] Template engine

## Concurrency & Parallelism
- [ ] Parallel map-reduce (Arc, Mutex, threads)
- [ ] Web crawler with thread pool
- [ ] Producer-consumer with channels
- [ ] Fork-join parallel merge sort
- [ ] Atomic counter examples
- [ ] Lock-free stack (Arc, atomic operations)
- [ ] Parallel prime sieve
- [ ] Concurrent hash map
- [ ] Actor system basics (channels)
- [ ] Work-stealing queue
- [ ] Barrier synchronization
- [ ] Read-write lock usage patterns

## File & I/O
- [ ] Log file analyzer (BufReader, error handling)
- [ ] File deduplicator (hashing, file system)
- [ ] Binary file parser (reading structs, unsafe transmute)
- [ ] Directory tree walker (recursion, Result)
- [ ] Config file loader with defaults (JSON/TOML)
- [ ] Streaming large file processing
- [ ] Tail -f implementation
- [ ] Compression/decompression wrapper
- [ ] Network packet parser
- [ ] Database connection pool mock

## Data Modeling & Type Safety
- [ ] Type-safe units system (newtype pattern)
- [ ] State machine with typestate pattern
- [ ] Builder pattern for complex objects
- [ ] Algebraic data types for domain (Option/Result variants)
- [ ] Phantom types for compile-time guarantees
- [ ] Type-level programming examples
- [ ] Safe FFI wrapper (unsafe in contained module)
- [ ] Zero-sized types for capabilities
- [ ] Validated types (email, phone, etc.)
- [ ] Finite state machine with enums

## Algorithms & Data Structure Classics
- [ ] Quicksort with different pivot strategies
- [ ] Merge sort (top-down and bottom-up)
- [ ] Heap sort
- [ ] Radix sort for integers
- [ ] KMP string matching
- [ ] Binary search with bounds
- [ ] Dynamic programming: knapsack problem
- [ ] Dynamic programming: edit distance
- [ ] Backtracking: N-Queens
- [ ] Greedy: interval scheduling
- [ ] Two pointers technique examples
- [ ] Sliding window problems

## Iterator & Functional Patterns
- [ ] Custom iterator for Fibonacci
- [ ] Iterator adapters chain (map, filter, fold)
- [ ] Lazy evaluation with closures
- [ ] IntoIterator for custom types
- [ ] DoubleEndedIterator implementation
- [ ] Peekable iterator usage
- [ ] Cycle and repeat patterns
- [ ] Zip and enumerate examples
- [ ] FlatMap and flatten usage
- [ ] Iterator collector patterns
- [ ] Scan accumulator patterns

## Smart Pointers & Interior Mutability
- [ ] Reference-counted cache (Rc<RefCell<T>>)
- [ ] Doubly-linked list (Rc + Weak)
- [ ] Tree with parent pointers (Weak)
- [ ] Shared mutable state (RefCell patterns)
- [ ] Cell for Copy types
- [ ] OnceCell for lazy initialization
- [ ] Arc for thread-safe sharing
- [ ] Cow (clone-on-write) patterns
- [ ] Box for recursive types
- [ ] Custom smart pointer with Drop

## Error Handling Patterns
- [ ] Custom error types with thiserror/anyhow patterns (manual)
- [ ] Error propagation with ?
- [ ] Result combinators (and_then, or_else, map_err)
- [ ] Early return patterns
- [ ] Collecting Results (Iterator<Item=Result>)
- [ ] Fallible iterator
- [ ] Error context wrapping
- [ ] Panic vs Result guidelines
- [ ] Option to Result conversion

## Trait System Mastery
- [ ] Polymorphism with trait objects (dyn)
- [ ] Static dispatch vs dynamic dispatch
- [ ] Trait bounds and where clauses
- [ ] Associated types vs generic parameters
- [ ] Default trait implementations
- [ ] Deriving traits (Clone, Debug, etc.)
- [ ] Operator overloading (Add, Mul, etc.)
- [ ] From/Into conversions
- [ ] Display and Debug formatting
- [ ] Custom iterator traits
- [ ] Deref coercion examples
- [ ] AsRef and AsMut patterns

## Memory & Performance
- [ ] Benchmark different collection strategies
- [ ] Avoid cloning with borrowing
- [ ] Lifetime elision examples
- [ ] Arena allocator
- [ ] Object pool pattern
- [ ] Struct layout and padding
- [ ] Bit packing structs
- [ ] Cache-friendly data structures
- [ ] SIMD operations (platform-specific)
- [ ] Memory profiling exercises

## Advanced/Misc
- [ ] Macro rules basics
- [ ] Declarative macros for DSL
- [ ] Conditional compilation (cfg)
- [ ] Feature flags usage
- [ ] Documentation with examples (doc tests)
- [ ] Property-based testing patterns
- [ ] Fuzzing harness
- [ ] WebAssembly target compilation
- [ ] Embedded no_std patterns
- [ ] Async/await basics (if including tokio)

## Project-Based Learning
- [ ] CLI tool: grep clone
- [ ] CLI tool: wc (word count) clone
- [ ] CLI tool: head/tail clone
- [ ] HTTP request library wrapper
- [ ] Simple web server (no frameworks)
- [ ] Chat server with websockets
- [ ] Database query builder
- [ ] Serialization library mini
- [ ] Compression library wrapper
- [ ] Image processing basics

## Additional Ideas from Curriculum

### Beginner-Friendly
- [ ] Hello Name (String vs &str ownership)
- [ ] Sum of squares (Vec basics, fold)
- [ ] Find min/max (Option, pattern matching)
- [ ] Reverse string (char iteration)
- [ ] Leap year checker
- [ ] GCD (Euclidean algorithm)
- [ ] Vector rotation

### Intermediate
- [ ] Two sum problem (HashMap lookups)
- [ ] Merge intervals
- [ ] Valid parentheses (stack)
- [ ] Queue using stacks
- [ ] Moving average stream
- [ ] Range sum query (prefix sums)
- [ ] Product of array except self
- [ ] Sliding window maximum

### Advanced Algorithms
- [ ] Pratt parser (precedence climbing)
- [ ] Shunting yard algorithm
- [ ] Fork-join merge sort
- [ ] Parallel prime sieve
- [ ] Work-stealing deque

### Ownership & Lifetime Specific
- [ ] Self-referential structs (Pin basics)
- [ ] Split at delimiter (returning slices)
- [ ] Lending iterator pattern
- [ ] Zero-copy parsing
- [ ] Ref splitting (split mutable borrows)

### Smart Pointer Specific
- [ ] Expression tree evaluator (Box recursion)
- [ ] Observer pattern (Weak references)
- [ ] Avoiding reference cycles
- [ ] Thread-safe counter (Arc<Mutex>)

### Trait-Specific
- [ ] Generic stack implementation
- [ ] Operator overloading (Add, Mul, Index)
- [ ] Static vs dynamic dispatch comparison

### Iterator-Specific
- [ ] Scan with accumulator
- [ ] Collect to different types
- [ ] Lazy evaluation with closures

### Concurrency-Specific
- [ ] Scoped threads for parallel map
- [ ] Barrier synchronization example
- [ ] RwLock for reader/writer pattern

### Type System Tricks
- [ ] Typestate pattern (compile-time state machine)
- [ ] Phantom types for units or capabilities
- [ ] Zero-sized type markers

### Real-World Mini Projects
- [ ] Grep with parallel file search
- [ ] Config file parser with defaults and validation
- [ ] Simple template engine
- [ ] Command-line calculator
- [ ] File watcher (tail -f)
- [ ] Log analyzer with statistics
