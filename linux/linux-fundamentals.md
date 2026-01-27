## **Module 1: Get a Linux Terminal**

**Goal**: A working Linux system and will have typed your first commands.

- **Linux** is an operating system kernel that controls your computer’s hardware and runs programs.
- You can’t talk to the kernel directly - you need a translator.
- The **shell** is that translator - a program that accepts your commands and communicates with the operating system.
- The shell starts when you log in and waits for your input.
- Commands like `ls` and `cat` are just programs that the shell finds and runs for you.
- A **terminal** is the window; the **shell** is what runs inside it.

## **Module 2: What is Linux?**

**Goal**: Do more things first, then understand what’s actually happening.

- **Linux** is an operating system kernel that controls your computer’s hardware and runs programs
- You can’t talk to the kernel directly - you need a translator
- The **shell** is that translator - a program that accepts your commands and communicates with the operating system
- The shell starts when you log in and waits for your input
- Commands like `ls` and `cat` are just programs that the shell finds and runs for you
- A **terminal** is the window; the **shell** is what runs inside it
- **CLI** means command-line interface - text-based interaction

You’re not just typing random commands anymore. You understand what’s happening: you type a command, the shell interprets it, finds the right program, runs it, and shows you the result.

## **Module 3: Package Management**

**Goal**: Install software and keep your system updated.

- **Packages** are bundles of software from trusted repositories
- **APT** is Ubuntu’s package manager
- **sudo** runs commands with administrator privileges
- Always run `apt update` before installing or upgrading
- `apt install` to add software, `apt remove` to remove it
- Installed htop, tree, curl, and vim for use in later modules

## **Module 4: Navigating the File System**

**Goal**: Move around confidently and understand how Linux organizes files.

- Linux has a single directory tree starting at `/`
- Key directories: `/home` (your files), `/etc` (config), `/var` (logs)
- Use `pwd` to see where you are, `cd` to move, `ls` to list
- `mkdir`, `touch`, `cp`, `mv`, `rm` for file operations
- `find` searches the file system, `locate` uses a database
- `type` is better than `which` for understanding commands
- Use `man` for documentation, `help` for shell builtins, `--help` for quick reference

## **Module 5: Reading and Viewing Files**

**Goal**: View file contents, search for text, and understand file information.

- `cat` for small files, `less` for large files
- `head` and `tail` for beginning and end
- `tail -f` to watch logs in real-time (essential for debugging)
- `grep` searches file contents - one of the most-used commands
- `file`, `stat`, `wc` tell you about files
- `du` for directory sizes, `df` for disk space

## **Module 6: Text Editing with Vi**

**Goal**: Edit files from the command line using the editor that’s available everywhere.

- Vi is everywhere - learn the basics, use them forever
- Two modes: Normal (commands) and Insert (typing)
- `i` to type, `Esc` to stop typing
- `:wq` to save and quit, `:q!` to abandon changes
- `hjkl` for navigation, `dd` to delete lines, `u` to undo
- BusyBox vi is what you’ll find in containers - no extras

With just these six commands, you can edit any file anywhere.

1. `i` - Start typing
2. `Esc` - Stop typing
3. `:wq` - Save and quit
4. `:q!` - Quit without saving
5. `dd` - Delete a line
6. `u` - Undo

## **Module 7: Users, Groups, and Permissions**

**Goal**: Understand who can access what on a Linux system.

- Every file has an owner (user), group, and permissions
- `adduser` creates users, `deluser` removes them
- Permissions: read ®, write (w), execute (x)
- Three sets: owner, group, others
- `chmod 600` = private, `chmod 644` = readable by all
- `sudo -u user` runs commands as another user
- Root can do anything - use `sudo` instead of being root

## **Module 8: Input/Output and Pipes**

**Goal**: Connect commands together and control where output goes.

- Programs have stdin (input), stdout (output), stderr (errors)
- `>` redirects stdout to file, `>>` appends
- `2>` redirects stderr, `&>` redirects everything
- `|` pipes output from one command to another
- Filter commands: `sort`, `uniq`, `cut`, `tr`, `tee`
- Interactive shells have a terminal; scripts don’t
- `/dev/null` discards output

## **Module 9: Processes and System**

**Goal**: Understand what’s running, manage processes, and control services.

- Every running program is a process with a PID
- `ps aux` shows all processes, `htop` is interactive
- `kill PID` stops a process, `kill -9` forces it
- Run commands in background with `&`, bring back with `fg`
- `systemctl` manages services: start, stop, enable, status
- `journalctl` views system logs
- `free -h`, `lscpu`, `lsblk` show system resources

## **Module 10: Networking and SSH**

**Goal**: Understand networking basics and master secure remote access with SSH.

- `ip addr` shows network interfaces, `ip route` shows routing
- `/etc/hosts` maps hostnames to IPs locally
- `ping` tests connectivity, `curl`/`wget` download files
- `ss -tuln` shows listening ports
- SSH keys are more secure than passwords
- `ssh-keygen` creates keys, `ssh-copy-id` installs them
- `ssh -v` shows which authentication method is used
- Disable password auth in `/etc/ssh/sshd_config` after key auth works
- `~/.ssh/config` simplifies SSH commands
- `scp` copies files securely between machines

## **Module 11: Tmux**

**Goal**: Keep your terminal sessions alive and organize your workspace with multiple panes and windows.

- Tmux keeps sessions alive when you disconnect
- Start with `tmux`, detach with `Ctrl+b d`, reattach with `tmux attach`
- Use named sessions: `tmux new -s name`
- Windows are tabs: `Ctrl+b c` creates, `Ctrl+b n/p` navigates
- Panes split windows: `Ctrl+b %` vertical, `Ctrl+b "` horizontal
- The prefix `Ctrl+b` starts all tmux commands

## **Module 12: Your Terminal Setup**

**Goal**: Transform your terminal from functional to professional with custom configuration files.

- Dotfiles (files starting with `.`) configure your environment
- `.bashrc` runs for interactive shells, `.profile` for login shells
- Starship gives you a modern, informative prompt with git status
- `.vimrc` makes vim much more usable with syntax highlighting and line numbers
- `.tmux.conf` customizes tmux (consider changing prefix to `Ctrl+a`)
- Back up your dotfiles in a git repository for portability
