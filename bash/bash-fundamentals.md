## **Module 1: Your First Script**

**Goal**: Go from zero to running bash scripts with security awareness.

- Use `#!/bin/bash` (not `#!/usr/bin/env bash`) for security
- Make scripts executable with `chmod +x`
- Never add `.` to your PATH
- Use `bash -x` to debug scripts
- **Run shellcheck on every script**

## **Module 2: Variables and Quoting**

**Goal**: Learn how to store and manipulate data in bash scripts safely. Master quoting rules to avoid security vulnerabilities - this is where most bash bugs come from.

- **Variables**: Assign with `=` (no spaces), access with `${}`
- **Double quotes**: Variables expand, spaces preserved - **use by default**
- **Single quotes**: Everything literal - use for exact strings
- **No quotes**: Dangerous - causes word splitting and glob expansion
- **Command substitution**: `$(command)` captures output
- **Special variables**: `$1` for arguments, `$?` for exit codes, `$@` for all args
- **Environment variables**: Don’t store secrets in them - use files instead

## **Module 3: Parameter Expansion**

**Goal**: Master parameter expansion - the skill that separates bash professionals from beginners. Learn to manipulate strings without spawning external processes.

- **Parameter expansion** replaces the need for sed, awk, cut in most cases
- **Default values**: `${var:-default}` and `${var:=default}`
- **String length**: `${#var}`
- **Remove suffix**: `${var%pattern}` (shortest), `${var%%pattern}` (longest)
- **Remove prefix**: `${var#pattern}` (shortest), `${var##pattern}` (longest)
- **Search/replace**: `${var/old/new}` (first), `${var//old/new}` (all)
- **Case change**: `${var^^}` (upper), `${var,,}` (lower)
- **Order matters**: Brace expansion happens before variable expansion

## **Module 4: Conditionals and Logic**

**Goal**: Learn to make decisions in your scripts safely. Master exit codes, logical operators, and why double brackets are mandatory for security.

- **Exit codes**: 0 = success, non-zero = failure, check with `$?`
- **&& (AND)**: Run next command only if previous succeeded
- **|| (OR)**: Run next command only if previous failed
- **[[ ]]**: Always use double brackets for tests (NEVER single brackets)
- **String tests**: `==`, `!=`, `-z`, `-n`
- **Numeric tests**: `-eq`, `-ne`, `-gt`, `-lt`, `-ge`, `-le`
- **File tests**: `-f`, `-d`, `-e`, `-r`, `-w`, `-x`
- **command -v**: Check if a command exists (NOT `which`)
- **case statements**: Pattern matching with `case/esac`

## **Module 5: Loops**

**Goal**: Learn to repeat actions efficiently. Master for loops, while loops, and the safe patterns for processing files.

- **For loops**: `for item in list; do ... done` - iterate over lists
- **While loops**: `while condition; do ... done` - run while true
- **Reading files**: `while read -r line; do ... done < file` - line by line
- **Break**: Exit loop immediately
- **Continue**: Skip to next iteration
- **File globs**: Use `*.txt` not `$(ls *.txt)` - handles spaces correctly
- **Check file exists**: `[[ -f "$file" ]] || continue` in loops
- **Always use** `read -r`: Prevents backslash interpretation

## **Module 6: Functions and Arrays**

**Goal**: Learn to organize code with functions and store lists of data in arrays.

- **Functions**: `name() { ... }` - reusable code blocks
- **Local variables**: `local var=value` - keep variables inside functions
- **Return values**: Exit codes for success/failure, `echo` for data
- **Arrays**: `arr=("a" "b")`, loop with `for x in "${arr[@]}"`

## **Module 7: Unix Filters and Editor Integration**

**Goal**: Learn to write small, composable tools that work with your editor. This is how I actually use bash day-to-day.

- Unix filters read stdin, write stdout, do one thing
- Keep filters small - 1-3 lines is ideal
- Put them in `~/.local/bin` for global access
- Use `!!` in vim to run them on current line
- This is how you extend your editor with bash

I write these tiny scripts constantly. They take 30 seconds to write and save hours over time.

1. **Speed** - `!!gendate` is faster than typing the date
2. **Accuracy** - No typos in date formats
3. **Composability** - Chain them together
4. **Editor integration** - Your scripts work inside vim

This is the Unix way. Small tools. Text in, text out. Everything composes.
