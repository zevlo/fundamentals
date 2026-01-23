## **Module 1: Your First Script**

**Goal**: Go from zero to running bash scripts with security awareness.

- Use `#!/bin/bash` (not `#!/usr/bin/env bash`) for security
- Make scripts executable with `chmod +x`
- Never add `.` to your PATH
- Use `bash -x` to debug scripts
- **Run shellcheck on every script**

Bash has variables, conditionals, loops, and functions. It’s not just a command runner - it’s a scripting language that’s on every Linux server.

**Why bash over zsh/fish?** Bash is the standard. When you SSH into a server, it’s running bash. Write portable scripts that work everywhere.

**Why write scripts?** Instead of typing commands one by one, write them once and run whenever needed. Automation, repeatability, documentation.

## **Definitions**

**Shebang**: The `#!` line specifying which interpreter runs the script.
**Shellcheck**: Static analysis tool for shell scripts - use it on everything.
**Symbolic link (symlink)**: A file that points to another file. Changes to the target are reflected through the link.
**Dotfiles**: Configuration files in your home directory (named with a leading dot, like `.bashrc`). Storing them in a `~/dotfiles/` directory with symlinks makes them portable and version-controllable.
