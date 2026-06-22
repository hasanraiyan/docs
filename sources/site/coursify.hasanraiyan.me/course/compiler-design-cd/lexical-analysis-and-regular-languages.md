# Source: https://coursify.hasanraiyan.me/course/compiler-design-cd/lexical-analysis-and-regular-languages

# Lexical Analysis and Regular Languages

35 mins

Understand how a scanner (lexer) reads a stream of characters and groups them into meaningful tokens. Master regular expressions as the formal tool for defining token patterns.

### Learning Goals

- Define the terms token, lexeme, and pattern and explain how they relate.
- Write regular expressions for identifiers, integer literals, float literals, and keywords.
- Explain the role of the lexical analyzer in the compiler pipeline and what it returns to the parser.
- Describe how a lexer handles whitespace, comments, and errors.

---

### The Role of the Lexical Analyzer

The **Lexical Analyzer** (also called the _scanner_ or _lexer_) is the very first phase of a compiler. It acts as the interface between the raw source text and the parser. Instead of the parser reading characters one-by-one, it calls the lexer with a simple request: **`getNextToken()`**. The lexer does all the hard work of reading ahead, grouping characters, and returning a clean, structured token.

The lexer also interacts directly with the **Symbol Table** — when it encounters an identifier for the first time, it inserts an entry into the symbol table and returns a pointer to that entry as part of the token.

---

### Token, Lexeme, and Pattern — The Three Core Definitions

These three terms are constantly confused in exams. Here is the precise distinction:

| Term | Definition | Example (from `float position = 3.14`) |
| --- | --- | --- |
| **Pattern** | The rule (typically a regular expression) that describes a _class_ of valid lexemes. | `[0-9]+\.[0-9]+` |
| **Lexeme** | The actual sequence of characters in the source code that matches a pattern. | `3.14` |
| **Token** | The structured `<token-name, attribute-value>` pair returned to the parser. | `<num, 3.14>` |

A **token** has two parts:

- **Token-name:** A symbolic constant representing the category (e.g., `id`, `num`, `keyword`, `relop`).
- **Attribute-value:** Additional data, usually a pointer into the symbol table or the literal value itself.

**Example:** For the source fragment `position = initial + rate * 60`:

| Lexeme | Pattern Matched | Token Returned |
| --- | --- | --- |
| `position` | identifier pattern | `<id, ptr_to_position>` |
| `=` | assignment operator | `<assign>` |
| `initial` | identifier pattern | `<id, ptr_to_initial>` |
| `+` | addition operator | `<+>` |
| `rate` | identifier pattern | `<id, ptr_to_rate>` |
| `*` | multiplication operator | `<*>` |
| `60` | integer literal pattern | `<num, 60>` |

**Exam Question Example: Counting Tokens** A very common exam question (like PYQ 2024) asks you to count the total number of tokens in a statement. Consider: `while(count<=10) count = count + 1;`

1. `while` (keyword)
2. `(` (punctuation)
3. `count` (identifier)
4. `<=` (relational operator — single token via maximal munch)
5. `10` (integer literal)
6. `)` (punctuation)
7. `count` (identifier)
8. `=` (assignment operator)
9. `count` (identifier)
10. `+` (addition operator)
11. `1` (integer literal)
12. `;` (punctuation) **Total: 12 tokens.** Note that whitespace is discarded and not counted.

### Regular Expressions — The Language of Lexers

A **Regular Expression** (regex) is a compact notation for describing a set of strings, called a **regular language**. Every token class (identifiers, integers, keywords) can be described by a regular expression, making them the perfect formalism for specifying a lexer's rules.

#### Regular Expression Metacharacters

| Notation | Name | Meaning | Example |
| --- | --- | --- | --- |
| `a` | Literal | Matches the exact character `a`. | `a` matches `"a"` |
| `ab` | Concatenation | `a` followed by `b`. | `ab` matches `"ab"` |
| `a|b` | Alternation (Union) | Matches `a` **or** `b`. | `a|b` matches `"a"` or `"b"` |
| `a*` | Kleene Star | Zero or more repetitions of `a`. | `a*` matches `""`, `"a"`, `"aa"`, ... |
| `a+` | Plus | One or more repetitions of `a`. Equivalent to `aa*`. | `a+` matches `"a"`, `"aa"`, ... |
| `a?` | Optional | Zero or one occurrence of `a`. | `a?` matches `""` or `"a"` |
| `[abc]` | Character Class | Matches any single character in the set. | `[abc]` matches `"a"`, `"b"`, or `"c"` |
| `[a-z]` | Range | Matches any character in the range. | `[a-z]` matches any lowercase letter |
| `[^abc]` | Negated Class | Matches any character NOT in the set. | `[^"]` matches any char except `"` |
| `.` | Wildcard | Matches any single character except newline. | `.+` matches any non-empty string |

#### Operator Precedence (High to Low)

1. **Kleene Star / Plus / Optional** (`*`, `+`, `?`) — bind most tightly
2. **Concatenation** (implicit, no operator)
3. **Alternation** (`|`) — binds least tightly

So `ab*|c` parses as `(a(b*))|c`, not `a(b*|c)`.

### Building Token Patterns: From Digits to Full Identifiers

1. 1
 
 Step 1
 
 A Single Digit
 
 The most fundamental building block is a single decimal digit. We use a **character class** to match any one of the ten digit characters.
 
 **Pattern:** `[0-9]`
 
 **Matches:** `0`, `1`, `2`, ..., `9` **Does not match:** `a`, `10`, (space)
 
 This is read as: 'any single character in the range from `0` to `9`'.
 
2. 2
 
 Step 2
 
 An Integer Literal
 
 An integer is a sequence of **one or more** digits. We apply the `+` quantifier to our digit pattern.
 
 **Pattern:** `[0-9]+`
 
 **Matches:** `0`, `42`, `1000`, `007` **Does not match:** (empty string), `3.14`, `0xFF`
 
 The `+` means 'one or more', which is equivalent to writing `[0-9][0-9]*`.
 
3. 3
 
 Step 3
 
 A Float Literal (Basic)
 
 A floating-point number has an integer part, a decimal point, and a fractional part.
 
 **Pattern:** `[0-9]+\.[0-9]+`
 
 **Matches:** `3.14`, `0.5`, `100.001` **Does not match:** `3` (no decimal), `.14` (no integer part), `3.` (no fractional part)
 
 Note: the `.` inside `\.` is **escaped** — without the backslash, `.` is a wildcard and would match any character.
 
4. 4
 
 Step 4
 
 A Float Literal (with Scientific Notation)
 
 Real programs often write numbers in scientific notation (e.g., `1.5e-10`). We extend our pattern to make the exponent part **optional**.
 
 **Pattern:** `[0-9]+\.[0-9]+([eE][+-]?[0-9]+)?`
 
 **Breaking it down:**
 
 - `[0-9]+\.[0-9]+` — the mandatory decimal part
 - `([eE]` — optionally, the letter `e` or `E`
 - `[+-]?` — optionally, a `+` or `-` sign
 - `[0-9]+)?` — followed by one or more digits (the exponent value)
 
 **Matches:** `3.14`, `1.5e10`, `2.7E-3`, `0.001e+100`
 
5. 5
 
 Step 5
 
 An Identifier
 
 Most languages define an identifier as a sequence that **starts with a letter or underscore**, followed by any number of letters, digits, or underscores.
 
 **Pattern:** `[a-zA-Z_][a-zA-Z0-9_]*`
 
 **Breaking it down:**
 
 - `[a-zA-Z_]` — the first character must be a letter (upper or lower case) or an underscore.
 - `[a-zA-Z0-9_]*` — followed by **zero or more** letters, digits, or underscores.
 
 **Matches:** `x`, `position`, `rate_1`, `_temp`, `MyClass` **Does not match:** `1x` (starts with digit), `my-var` (hyphen not allowed), (empty)
 
6. 6
 
 Step 6
 
 A String Literal
 
 A C-style string literal is any sequence of characters (except a double quote or newline) enclosed in double quotes.
 
 **Pattern:** `"[^"\]*"`
 
 **Breaking it down:**
 
 - `"` — opening double-quote (literal)
 - `[^"\]*` — zero or more characters that are **not** a double-quote and **not** a newline
 - `"` — closing double-quote (literal)
 
 **Matches:** `"hello"`, `"x = 5"`, `""` (empty string) **Does not match:** `"hello` (unclosed), `"li\ ne"` (contains newline)
 

Identifiers

Integer LiteralsFloat LiteralsString LiteralsOperators & Punctuation

**Pattern:** `[a-zA-Z_][a-zA-Z0-9_]*`

| Lexeme | Valid? | Reason |
| --- | --- | --- |
| `position` | ✅ | Starts with letter, all alphanumeric |
| `_temp` | ✅ | Underscore is a valid start character |
| `x1` | ✅ | Letter start, digit after is fine |
| `1x` | ❌ | Cannot start with a digit |
| `my-var` | ❌ | Hyphen (`-`) is not in `[a-zA-Z0-9_]` |

⚠️ **Note:** Keywords like `if`, `while`, and `int` also match this pattern. The lexer must check a **keyword table** after matching an identifier to resolve the conflict. Keywords always win.

#### The Keyword-Identifier Conflict

This is one of the most common exam questions. Keywords like `if`, `while`, `int`, and `return` all match the identifier pattern `[a-zA-Z_][a-zA-Z0-9_]*`. So how does the lexer tell them apart?

**Two standard solutions:**

1. **Keyword table lookup (most common):** The lexer matches any sequence as an identifier first, then looks it up in a pre-populated keyword hash table. If found, it returns the keyword token instead of `<id>`.
2. **Separate regex rules:** The lexer spec lists keywords as separate, higher-priority rules that are tried before the identifier rule.

Both solutions rely on the same principle: **keywords always take priority over identifiers.** A programmer cannot use `if` as a variable name because the lexer will always classify it as a keyword token first.

more...

#### The Limits of Regular Expressions

Regular expressions are powerful, but they have a fundamental limitation: **they cannot count**. This means they cannot recognize:

- **Balanced parentheses:** `((()))` with arbitrarily deep nesting
- **Matched HTML/XML tags:** `<b>...</b>`
- **Recursive structures** of any kind

Formally, these languages are **not regular** — they are **context-free**. This is precisely why we need a separate **Syntax Analyzer (Parser)** in Phase 2 that uses a Context-Free Grammar and a push-down automaton to handle these nested structures. Regular expressions are exactly strong enough for token recognition — no more, no less.

more...

### Common Questions

What does the lexer do with whitespace and comments?

What happens when the lexer encounters a character it cannot match?

Why not just use the parser to do the lexer's job?

### Knowledge Check

Question 1 of 6

Q1Single choice

The actual sequence of characters in the source code that matches a pattern (e.g., the string 'position') is called a:

Token

Pattern

Lexeme

Symbol

BackNext

[Compilers: Principles, Techniques & Tools (Dragon Book) — Chapter 3\\ \\ web](https://www.pearson.com/en-us/subject-catalog/p/compilers-principles-techniques-and-tools/P200000003268)

[Previous\\ \\ Phases of Compilation](https://coursify.hasanraiyan.me/course/compiler-design-cd/phases-of-compilation) [Next\\ \\ Finite Automata — NFA and DFA](https://coursify.hasanraiyan.me/course/compiler-design-cd/finite-automata-nfa-and-dfa)