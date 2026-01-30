# Bash

## Useful Links

- [How To Write Bash Scripts In Linux - Complete Guide](https://www.youtube.com/watch?v=2733cRPudvI&list=PLT98CRl2KxKGj-VKtApD8-zCqSaN2mD4w&index=1)

## Useful Commands & Functions

### File & Directory Management

- `ls` — List directory contents (`-l` for details; `<path>` to use it elsewhere; `-lah` for hidden files with permissions)
- `pwd` — Print current directory
- `cd <dir>` — Change directory
- `cd ~` — Go to home directory
- `cd /` — Go to root directory
- `tree` — Display directory tree (if installed)
- `mkdir <dir>` — Create directory
- `rmdir <dir>` — Remove empty directory
- `rm <file>` — Remove file
- `rm -r <dir>` — Remove directory recursively (`<dir>*` for pattern matching)
- `cp <src> <dest>` — Copy file
- `cp -r <src> <dest>` — Copy directory
- `mv <src> <dest>` — Move / rename files or folders
- `touch <file>` — Create new file
- `stat <file>` — Show file information

### File Viewing & Editing

- `cat <file>` — Print file contents
- `less <file>` — Scrollable file view
- `more <file>` — Basic file view
- `head <file>` — First 10 lines
- `tail <file>` — Last 10 lines
- `tail -f <file>` — Follow file updates
- `nano <file>` — Terminal editor
- `vim <file>` — Advanced terminal editor
- `nano /etc/resolv.conf` — Edit file with nano
- `Ctrl + o` — Save in nano
- `cat /etc/resolv.conf` — View file (small)
- `less /etc/resolv.conf` — Interactive view (large)

### Searching & Text Processing

- `grep <pattern> <file>` — Search text
- `grep -r <pattern> <dir>` — Recursive search
- `find <path> -name "<pattern>"` — Find files
- `awk '{print $1}'` — Field-based processing
- `sed 's/old/new/g'` — Stream text replacement
- `sort` — Sort lines
- `uniq` — Filter duplicates
- `wc` — Word, line, byte count

### Permissions & Ownership

- `chmod 755 <file>` — Change permissions
- `chmod +x <file>` — Make executable
- `chown user:group <file>` — Change ownership
- `umask` — Default permission mask

### Processes & System

- `ps` — List processes
- `top` / `htop` — Process monitor
- `kill <pid>` — Terminate process
- `kill -9 <pid>` — Force kill
- `jobs` — Background jobs
- `bg` / `fg` — Resume jobs
- `time <command>` — Measure execution time

### Networking

- `ping <host>` — Test connectivity
- `curl <url>` — HTTP requests
- `wget <url>` — Download files
- `ssh user@host` — Remote login
- `scp <src> user@host:<dest>` — Secure copy

### Archives & Compression

- `tar -cvf file.tar <dir>` — Create archive
- `tar -xvf file.tar` — Extract archive
- `tar -czvf file.tar.gz <dir>` — Create gzip archive
- `tar -xzvf file.tar.gz` — Extract gzip archive
- `zip -r file.zip <dir>` — Create zip
- `unzip file.zip` — Extract zip

### Shell Features / Builtins

- `alias ll='ls -lah'` — Create alias
- `export ENV_NAME=ENV_NAME_VALUE` — Set environment variable
- `printenv` / `env` — Show environment variables
- `printenv PATH` — Show specific variable
- Command chaining: `apt update && apt install -y curl`
- Pipes: `ls -laR . | grep wget`
- Globbing / wildcards: `rm file*`, `rm -r folder*`
- `history | grep ssh` — Search command history
- `xargs -n1 < file.txt` — Run command for each line in file

## General Information

- Bash is a **Unix shell** and **command language**.
- Commands follow the pattern: `command [options] [arguments]`.
- **Everything is a file** in Unix (files, directories, devices).
- Case-sensitive by default.
- Use **tab completion** to speed up typing.
- Use `man <command>` or `<command> --help` for documentation.
- **Pipes (`|`)** send output of one command to another.
- **Redirection**:
  - `>` overwrite output
  - `>>` append output
  - `<` input from file
  - `2>` redirect stderr
- `&&` runs next command only if previous succeeds.
- `||` runs next command only if previous fails.
- `;` runs commands sequentially.
- Environment variables:
  - Set: `VAR=value`
  - Export: `export VAR=value`
  - Access: `$VAR`
- Common variables: `$HOME`, `$PATH`, `$USER`, `$PWD`.
- Scripts start with a **shebang**: `#!/bin/bash`.
- Make scripts executable: `chmod +x script.sh`.
- Variables are **untyped strings** by default.
- Quoting rules:
  - `'single quotes'` — literal
  - `"double quotes"` — allows variable expansion
  - `\` escapes characters
- Command substitution: `$(command)`
- Exit codes: `0` = success, non-zero = error (`$?`).
- Loops:
  - `for`, `while`, `until`
- Conditionals use `if`, `elif`, `else`, `fi`.
- Test expressions: `[ condition ]` or `[[ condition ]]`.

## Code Examples

### Variables

- `name="value"` — Assign variable
- `echo "$name"` — Use variable

### Conditionals

- `if [ "$a" -eq "$b" ]; then ... fi`
- Common tests:
  - `-f` file exists
  - `-d` directory exists
  - `-z` empty string
  - `=` string equality
  - `-eq`, `-ne`, `-lt`, `-gt` numeric comparison

### Loops

- `for i in {1..5}; do ... done`
- `while condition; do ... done`

### Functions

- `my_func() { commands; }`
- Call with `my_func`
