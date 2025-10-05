# Language Grammar (Capstone Subset)

This is the EBNF grammar for the language subset to be implemented in problem #101.

**Excluded from full grammar**: import/package statements, data declarations, pattern matching (match/case), let expressions, template literals.

## Lexical Elements

### Comments
```
comment        ::= '\' [^\r\n]*
```

### Literals
```
number         ::= integer | float | hexadecimal
integer        ::= [0-9]+
float          ::= [0-9]+ '.' [0-9]+
hexadecimal    ::= '0x' [0-9a-fA-F]+
string         ::= '"' ([^"\\] | '\\' .)* '"'
                 | "'" ([^'\\] | '\\' .)* "'"
boolean        ::= 'true' | 'false'
null           ::= 'null'
undefined      ::= 'undefined'
```

### Identifiers
```
identifier     ::= [a-zA-Z_][a-zA-Z0-9_]*
```

### Keywords
```
keywords       ::= 'var' | 'val' | 'def' | 'if' | 'then' | 'elif' | 'else'
                 | 'while' | 'do' | 'for' | 'loop' | 'break' | 'continue'
                 | 'return'
                 | 'true' | 'false' | 'null' | 'undefined' | 'NaN' | 'Infinity'
                 | 'and' | 'or' | 'not' | 'in' | 'instanceof' | 'mod' | 'step' | 'end' | 'typeof'
```

## Expressions

### Primary Expressions
```
primary        ::= identifier
                 | number
                 | string
                 | boolean
                 | null
                 | undefined
                 | NaN
                 | Infinity
                 | '(' expression ')'
                 | array_literal
                 | object_literal
                 | indented_block
                 | anonymous_function
                 | if_expression
                 | while_expression
                 | do_while_expression
                 | for_expression
                 | loop_expression
                 | break_expression
                 | continue_expression
                 | return_expression
```

### Literals
```
array_literal     ::= '[' (expression (',' expression)*)? ']'
object_literal    ::= '{' (property (',' property)*)? '}'
property          ::= identifier ':' expression
                    | string ':' expression
```

### Anonymous Functions
```
anonymous_function ::= identifier '->' expression                  // single parameter
                     | '(' ')' '->' expression                    // no parameters
                     | '(' parameters ')' '->' expression         // multiple parameters
parameters         ::= identifier (',' identifier)*
```

### Control Flow Expressions
```
if_expression  ::= 'if' expression 'then' expression elif_part* else_part?
                 | 'if' expression ['then'] indented_block elif_part* else_part? ['end' 'if']

elif_part      ::= [NEWLINE] 'elif' expression 'then' expression
                 | [NEWLINE] 'elif' expression ['then'] indented_block

else_part      ::= [NEWLINE] 'else' expression
                 | [NEWLINE] 'else' indented_block

while_expression ::= 'while' expression 'do' expression
                   | 'while' expression indented_block ['end' 'while']

do_while_expression ::= 'do' expression 'while' expression
                      | 'do' indented_block 'while' expression

for_expression ::= 'for' (var_decl | expression)? ';' expression? ';' expression?
                   ('do' expression | indented_block ['end' 'for'])

loop_expression ::= 'loop' expression
                  | 'loop' indented_block ['end' 'loop']
```

### Special Expressions
```
break_expression    ::= 'break'
continue_expression ::= 'continue'
return_expression   ::= 'return' expression?
```

### Postfix Expressions
```
postfix        ::= primary postfix_op*
postfix_op     ::= '(' arguments? ')'                     // function call, array/object indexing
                 | '.' identifier                        // property access
                 | '?.' identifier                       // optional chaining
                 | '++'                                  // postfix increment
                 | '--'                                  // postfix decrement
arguments      ::= expression (',' expression)*
```

**Note**: `arr(0)` is array indexing, `obj("key")` is object indexing - same syntax as function calls. Arrays and objects are callable values.

### Unary Expressions
```
unary          ::= postfix
                 | unary_op unary
unary_op       ::= '+' | '-' | '!' | 'not' | '~' | '++' | '--' | 'typeof'
```

### Binary Expressions (by precedence, highest to lowest)
```
power          ::= unary ('**' unary)*                   // right-associative
multiplicative ::= power (('*' | '/' | '//' | '%' | 'mod') power)*
additive       ::= multiplicative (('+' | '-') multiplicative)*
shift          ::= additive (('<<' | '>>' | '>>>') additive)*
range          ::= shift (('..' | '..<') shift ['step' shift])?
bitwise_and    ::= range ('&' range)*
bitwise_xor    ::= bitwise_and ('^' bitwise_and)*
bitwise_or     ::= bitwise_xor ('|' bitwise_xor)*
relational     ::= bitwise_or (('<' | '<=' | '>' | '>=' | 'in' | 'instanceof') bitwise_or)*
equality       ::= relational (('==' | '!=') relational)*
logical_and    ::= equality (('&&' | 'and') equality)*
logical_or     ::= logical_and (('||' | 'or') logical_and)*
null_coalesce  ::= logical_or ('??' logical_or)*
```

### Ternary Conditional
```
ternary        ::= null_coalesce ('?' ternary ':' ternary)?
```

### Assignment Expressions
```
assignment     ::= ternary assignment_op assignment
                 | ternary
assignment_op  ::= '=' | '+=' | '-=' | '*=' | '/=' | '//=' | '%=' | '**='
                 | '<<=' | '>>=' | '>>>=' | '&=' | '^=' | '|='
                 | '&&=' | '||=' | '??='
```

### Expression Definition
```
expression     ::= assignment
                 | anonymous_function
```

## Statements

### Variable Declarations
```
var_decl       ::= 'var' identifier ('=' expression)?
val_decl       ::= 'val' identifier '=' expression
```

### Function Declarations
```
function_decl  ::= 'def' identifier '(' parameters? ')' '=' expression
                 | 'def' identifier '(' parameters? ')' '=' indented_block ['end' identifier]
```

### Statement Types
```
statement      ::= var_decl
                 | val_decl
                 | function_decl
                 | expression_stmt

expression_stmt ::= expression
```

### Block and Program Structure
```
indented_block ::= NEWLINE INDENT block DEDENT

block          ::= (statement | expression)*

program        ::= block
```

## End Markers

Optional end markers for constructs with indented blocks:

- **Control flow**: `end if`, `end while`, `end for`, `end loop`
- **Function declarations**: `end <function_name>`

**Rules:**
- Only available with indented blocks (not single-line forms)
- `do...while` loops don't support end markers (self-delimiting)

## Language Semantics

### Expression vs Statement
- **Expressions** return values: control flow, arithmetic, literals, function calls
- **Statements** do not return values: declarations, expression statements

### Block Expression Semantics
Indented blocks are expressions that return:
1. The value of the last expression in the block, OR
2. `undefined` if the block ends with a statement, OR
3. `undefined` if the block is empty

### Scoping Rules
- Function parameters create local scope
- Variable declarations create local scope within current block
- Blocks create new local scopes
- Variable shadowing is allowed

### Indexing and Property Access
- `arr(0)` - Array indexing using call syntax
- `obj("key")` - Object indexing using call syntax
- `obj.name` - Property access using dot notation
- Arrays and objects are first-class values that can be called

## Operator Precedence (highest to lowest)

1. **Postfix**: `()` `.` `?.` `++` `--`
2. **Unary**: `+` `-` `!` `not` `~` `++` `--` `typeof` (prefix)
3. **Power**: `**` (right-associative)
4. **Multiplicative**: `*` `/` `//` `%` `mod`
5. **Additive**: `+` `-`
6. **Shift**: `<<` `>>` `>>>`
7. **Range**: `..` `..<` (with optional `step`)
8. **Bitwise AND**: `&`
9. **Bitwise XOR**: `^`
10. **Bitwise OR**: `|`
11. **Relational**: `<` `<=` `>` `>=` `in` `instanceof`
12. **Equality**: `==` `!=`
13. **Logical AND**: `&&` `and`
14. **Logical OR**: `||` `or`
15. **Null Coalescing**: `??`
16. **Ternary Conditional**: `? :`
17. **Assignment**: `=` `+=` `-=` `*=` `/=` `//=` `%=` `**=` `<<=` `>>=` `>>>=` `&=` `^=` `|=` `&&=` `||=` `??=`

## Implementation Notes

### Bytecode Design
- **CALL opcode** handles function calls, array indexing, and property access
- Runtime dispatch based on value type (Function/Array/Object)
- Enables arrays/objects to be passed wherever functions are expected

### Event Loop Built-ins
The following built-in functions are provided for asynchronous execution:
- `setTimeout(callback, delay)` - Schedule timer
- `setInterval(callback, delay)` - Recurring timer
- `setImmediate(callback)` - Next event loop iteration
- `nextTick(callback)` - End of current phase
- `clearTimeout(id)` - Cancel timeout
- `clearInterval(id)` - Cancel interval

---

This grammar defines an expression-oriented language where control flow constructs return values, similar to functional languages like Scala and ML.
