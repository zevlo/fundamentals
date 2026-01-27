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

**Goal**: Master parameter expansion - the skill that separates bash professionals from beginners.

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
