# Pythonic Arithmetic Parser in C  
  
## Goal
  
Write a C program that evaluates arithmetic expressions from text files using (mostly) Python’s operator rules and standard C (similar to Java) arithmetic semantics. The program must:  
* Read an input file (or a directory of files).  
* Parse and evaluate expressions.  
* Report either the numeric result or a precise error location.  
* Write the result to an output file with a specific naming convention.
  
## CLI & I/O
  
### Invocation   
  
`calc [-d DIR | --dir DIR] [-o OUTDIR | --output-dir OUTDIR] input.txt`  
* If ` -d/--dir ` is provided, process all ` *.txt files ` in DIR (ignore subfolders).  
* If ` -o/--output-dir ` is omitted, create a default output folder:  
` <input_base>_<username>_<studentid> `  
  Example: ` labs_valdis_12345/ `  
* If ` -o/--output-dir ` is provided and does not exist, create it.  
  
### Output file name
  
For each input `task1.txt`, produce:  
`task1_<name>_<lastname>_<studentid>.txt`  
The file contains either the result (single line) or `ERROR:<pos>.`  
> Character position is 1-based, counting every char in the file, including `\n` as one character.  
  
### Input Assumptions (Baseline)
  
* ASCII only.  
* Whitespace may appear anywhere.  
* At minimum (grade 4–6) inputs are single line ≤ 100 chars (later grades extend this).  
* Expressions can be integer and, for higher grades, float (IEEE 754 double).  
  
## Features by Grade (Rubric)  
  
### Grade 4/10 — Minimal Pass  
  
* Single line (≤ 100 chars).  
* Integers only (base-10, optional leading `+`/`-`).  
* Operators: `+` `-` (binary).  
* Output: numeric result (as integer text).  
* On any parse/eval error: `ERROR:<pos>` (1-based char index).  
    
### Grade 5/10 — Positioned Errors  
  
* Same as Grade 4 plus:  
* Accurate error position: if the first error is at character 57, output `ERROR:57`.   
  * Examples of errors: invalid token, unexpected end, two operators in a row, leading operator without operand, etc.  
  
### Grade 6/10 — Multiplication (+ optional floats)  
  
* Add `*` (binary).
* Additional challenge: support floats (64-bit) mixed with ints.
  * If floats are supported, print using `%.15g` (see Output formatting below).
* Still single line ≤ 100 chars.
  
### Grade 7/10 — Division (+ big files challenge)

* Add `/` (true division if floats supported; otherwise integer division).  
* Division by zero ⇒ `ERROR:<pos>` where `<pos>` is the starting char index of the offending divisor token (or the `/` token—either is acceptable if documented).  
* Additional challenge: allow multiple lines and inputs up to 10,000 characters total.  
  
### Grade 8/10 — Parentheses  
  
* Add `(` `)` with correct precedence and associativity.  
* Error reporting must still work (unmatched paren should point to the problematic paren or place where the closing/opening was expected).  
  
### Grade 9/10 — Comments & Batch Mode   
  
* Ignore full lines that start with `#` (Pythonic line comments).  
* Support `-d/--dir` to process all `*.txt` in a folder.  
* Support `-o/--output-dir` to choose/create output folder.  
* Default folder behavior when `-o` not provided as specified above.  
  
### Grade 10/10 — Exponentiation & No Input Size Guarantees  
  
* Add Python power operator: `**`  
  * Right-associative (e.g., `2**3**2 == 2**(3**2) == 512`).  
  * Higher precedence than `*` `/` and `+` `-`.  
  * Precedence is just below unary operators (if you implement unary; see below).  
* No specific length limits beyond “fits in Codespaces VM” (i.e., handle very long files efficiently).  
* Maintain all prior features and error reporting.  

