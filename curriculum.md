# Rust Learning Curriculum - 101 Problems

Problems ordered from foundational to advanced. Each builds on previous concepts while introducing new ones.

## Phase 1: Foundations (1-15)
Basic syntax, ownership, borrowing, simple collections

1. **RPN Calculator** - String vs &str, Vec as stack, Result, pattern matching, parsing
2. **Sum of Squares** - Vec basics, iteration, fold
3. **Palindrome Checker** - String iteration, chars vs bytes
4. **Find Min/Max** - Option, pattern matching, slice iteration
5. **Word Counter** - HashMap basics, String splitting
6. **Unique Elements** - HashSet, collecting
7. **Fizzbuzz** - Range iteration, match/if expressions
8. **Reverse String** - String mutation, chars, collect
9. **Caesar Cipher** - Char manipulation, wrapping arithmetic
10. **Vector Rotate** - Vec mutation, borrowing
11. **Leap Year** - Functions, boolean logic, match
12. **Greatest Common Divisor** - Recursion vs iteration, borrowing
13. **Prime Checker** - Loops, early returns, optimization
14. **Fibonacci Iterator** - Custom iterator basics
15. **Anagram Groups** - HashMap<String, Vec<String>>, sorting

## Phase 2: Intermediate Collections (16-30)
More complex collection usage, error handling

16. **Top K Frequent** - BinaryHeap usage
17. **LRU Cache** - HashMap + VecDeque or custom linked list
18. **Two Sum** - HashMap for lookups
19. **Merge Intervals** - Vec sorting, iteration
20. **Valid Parentheses** - Vec as stack
21. **Queue with Stacks** - VecDeque or Vec manipulation
22. **Circular Buffer** - VecDeque or custom ring buffer
23. **Moving Average** - VecDeque, running calculations
24. **Sparse Matrix** - HashMap<(usize, usize), T>
25. **Frequency Sort** - BinaryHeap with custom Ord
26. **Group Anagrams** - HashMap with computed keys
27. **Intersection of Lists** - HashSet operations
28. **Range Sum Query** - Prefix sums, Vec
29. **Product Except Self** - Vec transformations
30. **Sliding Window Max** - VecDeque as deque

## Phase 3: Error Handling & I/O (31-40)
Result, Option, file operations

31. **Safe Division** - Result basics, custom errors
32. **Parse Config** - Result chaining, ? operator
33. **File Line Counter** - BufReader, io::Result
34. **CSV Parser** - Split, Result collection
35. **Error Propagation** - Multiple error types, map_err
36. **Option Chaining** - Combinators (and_then, or_else)
37. **Read JSON-like** - Recursive Result, Box<dyn Error>
38. **Fallible Iterator** - Iterator<Item=Result<T, E>>
39. **Log Parser** - Regex-like, custom error types
40. **Config Loader** - Default values, Result unwrap patterns

## Phase 4: Ownership Deep Dive (41-50)
Borrowing, lifetimes, Cow

41. **String Interner** - Rc<str>, HashMap, reference counting
42. **Borrow vs Own** - Performance comparison, Cow
43. **Lifetime Annotations** - Explicit lifetimes in structs
44. **Self-Referential** - Why it's hard, Pin basics
45. **Split at Delimiter** - Returning slices with lifetimes
46. **Iterator Lending** - Lifetime challenges
47. **Cow Pattern** - Clone on write, string/slice
48. **Zero-Copy Parser** - &str slicing, avoiding allocation
49. **Arena Allocator** - Vec-based arena, indices vs refs
50. **Ref Splitting** - Split borrows, multiple mut refs

## Phase 5: Smart Pointers (51-65)
Box, Rc, RefCell, Arc, Weak

51. **Linked List** - Box<Node> for recursive type
52. **Binary Tree** - Box for children
53. **Expression Tree** - Recursive enum with Box
54. **Shared List** - Rc for multiple owners
55. **Doubly Linked List** - Rc + Weak for back pointers
56. **Tree with Parents** - Weak for parent pointers
57. **Graph Adjacency** - Vec<Rc<RefCell<Node>>>
58. **Interior Mutability** - RefCell for shared mutation
59. **Cache with Eviction** - Rc<RefCell<T>>, shared mutable
60. **Observer Pattern** - Weak for observers, Rc for observed
61. **Reference Cycles** - Understanding and avoiding
62. **Thread-Safe Counter** - Arc<Mutex<usize>>
63. **Shared State Threads** - Arc for sharing across threads
64. **Thread-Safe Cache** - Arc<Mutex<HashMap>>
65. **Custom Smart Pointer** - Deref, Drop traits

## Phase 6: Trait System (66-75)
Traits, generics, associated types

66. **Generic Stack** - Generic type parameter
67. **Trait Bounds** - where clauses, multiple bounds
68. **Comparable** - Implementing Ord, PartialOrd
69. **Display Format** - Display and Debug traits
70. **From/Into** - Conversion traits
71. **AsRef Pattern** - Generic over string-like types
72. **Trait Objects** - dyn Trait, dynamic dispatch
73. **Static vs Dynamic** - Performance comparison
74. **Associated Types** - Iterator pattern, Graph trait
75. **Operator Overload** - Add, Mul, Index traits

## Phase 7: Advanced Patterns (76-85)
Iterators, closures, advanced techniques

76. **Custom Iterator** - IntoIterator, Iterator trait
77. **DoubleEnded Iterator** - Next and next_back
78. **Peekable Parser** - Using Peekable iterator
79. **Lazy Evaluation** - Closures for deferred computation
80. **Iterator Adapters** - Chaining map, filter, flat_map
81. **Collect Patterns** - Different FromIterator targets
82. **Scan Accumulator** - Stateful iteration
83. **Builder Pattern** - Method chaining, typestate
84. **Newtype Pattern** - Type safety with wrappers
85. **Phantom Types** - Compile-time state tracking

## Phase 8: Concurrency (86-92)
Threads, channels, sync primitives

86. **Parallel Sum** - Thread spawn, join
87. **Producer Consumer** - Channels, mpsc
88. **Thread Pool** - Manual thread pool implementation
89. **Parallel Map** - Scoped threads, Arc
90. **Work Stealing** - VecDeque, Mutex, complex coordination
91. **Barrier Sync** - Barrier usage
92. **RwLock Pattern** - Read-write lock for readers/writers

## Phase 9: Real-World Algorithms (93-100)
Classic algorithms with Rust flavor

93. **Dijkstra's Path** - BinaryHeap, HashMap, graph
94. **Topological Sort** - DFS with state tracking
95. **Union Find** - Disjoint set with path compression
96. **Trie Autocomplete** - Recursive structure, prefix search
97. **KMP Matching** - State machine, prefix function
98. **Edit Distance** - 2D DP with Vec<Vec<usize>>
99. **N Queens** - Backtracking with mutable state
100. **Sudoku Solver** - Backtracking, bit manipulation

## Phase 10: Capstone (101)

101. **Compiler + VM** - Subset implementation based on provided grammar (excluding import/package/data):

    **Compiler Frontend:**
    - **Lexer**: Custom iterator over chars, tokenization
      - Keywords: var, val, def, if, then, elif, else, while, do, for, loop, break, continue, return
      - Operators: All binary/unary ops, assignment variants
      - Literals: numbers (int/float/hex), strings, booleans, null, undefined
      - Comments (backslash-style)

    - **Parser**: Recursive descent, Pratt parsing for expressions
      - AST nodes with Box for recursive expressions
      - Expression-oriented: blocks return values
      - Operator precedence (17 levels)
      - Indented blocks (INDENT/DEDENT tokens)
      - Anonymous functions: `x -> x + 1`, `(a, b) -> a + b`
      - Control flow as expressions (if/while/for/loop all return values)

    - **Semantic Analysis**:
      - Symbol tables (HashMap) for variable scoping
      - Scope stack for nested blocks
      - Variable shadowing rules
      - Break/continue context validation
      - Return statement validation

    **Compiler Backend:**
    - **Bytecode Generation**:
      - Instruction set: LoadConst, LoadVar, StoreVar, Add, Sub, Mul, Div, etc.
      - Jump instructions for control flow
      - Call/Return for functions and indexing (unified)
      - Closure creation instructions
      - Note: `arr(0)` and `obj.field` both compile to CALL opcode
      - Arrays/objects are first-class callable values
    - **Constant Pool**: Deduplicated string/number literals (Rc<str>)
    - **Code Object**: Bytecode + metadata
    - **Error Reporting**: Line/column info, helpful messages

    **Virtual Machine:**
    - **Stack-based execution**: Vec<Value> for operands
    - **Call frames**: Vec of frames (locals, return address, closure env)
    - **Value type**: Enum for Number/String/Bool/Null/Array/Object/Function/Closure
    - **Heap objects**: Rc<RefCell<T>> for arrays/objects (shared, mutable)
    - **Closures**: Capture environment with Rc<RefCell<Environment>>
    - **Instruction dispatch**: Large match on OpCode enum
    - **Built-ins**: print, type_of, array/object creation
    - **Debug mode**: Trace execution, disassembler

    **Event Loop (Mini Node.js style):**
    - **Event queue**: VecDeque<Event> for pending events
    - **Timer heap**: BinaryHeap for scheduled callbacks (setTimeout, setInterval)
    - **Event types**: Timer, IO (simulated), Immediate, NextTick
    - **Microtask queue**: VecDeque for high-priority tasks (nextTick, promises)
    - **Phase-based execution**: Timers → IO → Immediates → Close callbacks
    - **Callback registry**: HashMap<EventId, Closure> for event handlers
    - **Non-blocking**: VM yields control between events
    - **Built-in async functions**:
      - `setTimeout(callback, delay)` - Schedule timer
      - `setInterval(callback, delay)` - Recurring timer
      - `setImmediate(callback)` - Next iteration
      - `nextTick(callback)` - Current phase end
      - `clearTimeout(id)`, `clearInterval(id)` - Cancel timers
    - **Event loop phases**:
      1. Execute expired timers
      2. Execute I/O callbacks (simulated file/network)
      3. Execute setImmediate callbacks
      4. Process nextTick queue between phases
    - **Loop termination**: Exit when no pending events/timers

    **Language Features to Implement:**
    - Variables: `var x = 10`, `val y = 20` (immutable)
    - Functions: `def add(a, b) = a + b`
    - Anonymous functions: `(x, y) -> x * y`
    - Closures: Functions capturing outer scope
    - Arrays: `[1, 2, 3]`, indexing `arr(0)` (function call syntax)
    - Objects: `{name: "Alice", age: 30}`, property access `obj.name`
    - Control flow: if/elif/else, while, do-while, for, loop
    - All operators: arithmetic, logical, bitwise, comparison, assignment
    - Blocks as expressions: Last expression is return value

    **Rust Concepts Exercised:**
    - **Enums**: Token, AstNode, OpCode, Value, BinaryOp, UnaryOp, Event, EventPhase
    - **Box**: Recursive AST (Box<Expr> in BinaryExpr)
    - **Rc/RefCell**: Closures (Rc<RefCell<Environment>>), heap objects, shared event handlers
    - **HashMap**: Symbol tables, object properties, constant pool, event callbacks
    - **Vec**: Token stream, bytecode, operand stack, call stack, arrays
    - **VecDeque**: Event queue, microtask queue (FIFO operations)
    - **BinaryHeap**: Timer scheduling (priority queue by time)
    - **String vs &str**: Identifiers, string literals, interning
    - **Custom error types**: LexError, ParseError, RuntimeError with spans
    - **Result/Option**: Error propagation throughout
    - **Pattern matching**: AST traversal, instruction dispatch, event handling
    - **Iterators**: Lexer (chars iterator), peekable for parser
    - **Traits**: Display for AST/values, custom Debug, Ord for timer heap
    - **Lifetimes**: Parser borrowing source, AST node references
    - **Performance**: Avoiding clones, Rc vs Box choices, constant pooling
    - **Time handling**: std::time::{Duration, Instant} for timers

    **Implementation Phases:**
    1. Lexer: Tokenize basic literals and operators
    2. Parser: Expression parsing with precedence
    3. Evaluator: Tree-walk interpreter (simpler than VM)
    4. Bytecode compiler: Lower AST to bytecode
    5. VM: Execute bytecode with stack machine
    6. Functions and closures
    7. Collections (arrays, objects)
    8. Control flow (if/while/for/loop as expressions)
    9. Event loop: Timer queue, event phases, async built-ins
    10. Error recovery and debugging tools

    **Example Event Loop Code:**
    ```javascript
    \ Demonstrates async execution
    var counter = 0

    def tick() =
        counter = counter + 1
        print(`Tick: $counter`)

    setTimeout(() -> print("First timer"), 100)
    setInterval(tick, 50)
    setTimeout(() -> print("Second timer"), 200)
    setImmediate(() -> print("Immediate!"))
    nextTick(() -> print("Next tick!"))

    print("Synchronous code done")
    \ Event loop keeps running until all timers cleared
    ```

---

## Concepts Coverage Checklist

### Collections
- [x] Vec, HashMap, HashSet, BTreeMap, BinaryHeap, VecDeque
- [x] Strings (String, &str, Rc<str>)

### Ownership & Borrowing
- [x] Move semantics, borrowing rules, lifetimes
- [x] Cow (clone on write)

### Smart Pointers
- [x] Box, Rc, RefCell, Arc, Weak, Mutex

### Error Handling
- [x] Option, Result, ? operator, custom errors

### Traits
- [x] Standard traits (Clone, Debug, Display, From/Into)
- [x] Custom traits, trait bounds, trait objects
- [x] Associated types vs generics

### Iterators
- [x] Iterator, IntoIterator, custom iterators
- [x] Adapters and combinators

### Concurrency
- [x] Threads, channels, Arc, Mutex, RwLock

### Advanced
- [x] Closures, pattern matching, enums
- [x] Typestate, phantom types, newtype
- [x] Builder pattern, interior mutability

## Learning Approach

Each problem should include:
1. **Problem statement** - Clear requirements
2. **Learning goals** - What Rust concepts it teaches
3. **Starter code** - Type signatures, scaffolding
4. **Hints** - Progressive hints if stuck
5. **Multiple solutions** - Idiomatic vs beginner-friendly
6. **Tests** - Comprehensive test cases
7. **Follow-up** - Extension challenges

## Success Metrics

By problem 101, you should be able to:
- Choose the right collection for any problem
- Use borrowing to avoid clones
- Apply smart pointers appropriately
- Write idiomatic iterators and trait implementations
- Handle errors gracefully
- Write thread-safe concurrent code
- Read and understand real Rust codebases
