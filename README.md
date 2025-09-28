# PA3 - Simple Interpreter

**Due: Monday, Oct 6 at 11:59 PM**

## Overview

In this assignment, you will implement simple interpreters using PLCC. You'll work with recursive data structures and implement evaluation semantics for basic languages.

## Q1: LONN (List of Non-empty Numbers)

**Starter files**: `q1/lonn.grammar`

LONN is a language for a nonempty-list-of-numbers. Implement the **minimum-value semantics** for this language. When a LONN program is evaluated, it should display the minimum value in the list.

### Example Session

```
--> (3)
3
--> (3 5 2 4)
2
--> ()
ERROR
```

### Implementation Notes

- The LONN grammar defines lists recursively
- Your semantics will use functional recursion to traverse the structure
- Compute and return the minimum value from the list

### Testing

Create a test file with sample inputs and use:

```bash
plccmk -c lonn.grammar
rep -n < tests.lonn
```

## Q2: Binary Numbers

**Starter files**: `q2/binary.grammar`

Write a lexical specification and semantics for unsigned binary numbers. The language should output the decimal value of the given binary number.

### Example Session

```
--> 0
0
--> 101
5
--> 000000011
3
--> 10000
16
--> 11111
31
--> 012
ERROR
```

### Requirements

**Lexical Specification**:

- Three tokens: `NL` (newline as `'\n'`), `ZERO`, and `ONE`

**Syntactic Specification**:

- Add two grammar rules for `<bit>` non-terminal
- One rule for `ZERO`, one for `ONE`
- Define appropriate subclass names for the Bit class

**Semantic Specification**:

- `$run()` in `Binary`: prints result of `bits.eval()`
- `eval()` in `Bits`: calculates decimal value using accumulator pattern
- Abstract `eval()` in `Bit` returning int
- Concrete `eval()` in Bit subclasses returning 0 or 1

### Algorithm

Use accumulator pattern to convert binary to decimal:

1. Initialize sum to 0
2. For each bit from left to right:
   - Multiply current sum by 2
   - Add current bit value to sum

Example: `1011` → `((0×2+1)×2+0)×2+1)×2+1 = 11`

### Error Handling

If `bitList` is empty, throw a `PLCCException` with appropriate message.

## Submission

**To Submit:**

1. Complete all questions, including written answers in this README
2. Test your grammars to ensure they work correctly
3. From inside your container: `tar -czf /workspace/pa3-YOURNAME.zip /workspace`
4. Download and submit the zip file to Kodiak

**Grading Criteria:**

- **Submission (33.3%):** Files are properly named and located as specified
- **Completeness (33.3%):** All questions attempted (incomplete = incorrect)
- **Correctness (33.3%):** Solutions demonstrate understanding of syntax specifications

**Late Policy:** 10% per day, maximum 5 days late

---

_Course content developed by Declan Gray-Mullen for WNEU with Claude_
