# Bash Guide: From Beginner to Advanced

## 1. Introduction to Bash

Bash (Bourne Again Shell) is a Unix shell and command language. It is widely used for scripting and automating tasks in Linux and macOS environments.

---

## 2. Setting Up Bash

### On Linux

Bash is pre-installed on most Linux distributions. Open a terminal to start using it.

### On macOS

Bash is pre-installed. Open the Terminal app to use it.

### On Windows

1. Install [Git for Windows](https://git-scm.com/) to get Git Bash.
2. Alternatively, enable the Windows Subsystem for Linux (WSL) and install a Linux distribution.

---

## 3. Basic Bash Commands

### Navigating the Filesystem

- `pwd` - Print the current working directory.
- `ls` - List files and directories.
- `cd` - Change directory.

### File Operations

- `touch` - Create an empty file.
- `cp` - Copy files or directories.
- `mv` - Move or rename files or directories.
- `rm` - Remove files or directories.

### Viewing File Contents

- `cat` - Concatenate and display file contents.
- `less` - View file contents one screen at a time.
- `head` - Display the first few lines of a file.
- `tail` - Display the last few lines of a file.

---

## 4. Working with Files and Directories

- Wildcards: `*`, `?`, `[abc]`
- Permissions: `chmod`, `chown`
- Archiving and Compression: `tar`, `gzip`, `zip`

---

## 5. Bash Scripting Basics

### Creating a Script

1. Create a file with a `.sh` extension.
2. Add the shebang: `#!/bin/bash`
3. Write your commands.

### Running a Script

- Make it executable: `chmod +x script.sh`
- Run it: `./script.sh`

---

## 6. Control Structures in Bash

### Conditional Statements

- `if`, `else`, `elif`
- Example:
  ```bash
  if [ condition ]; then
      echo "Condition is true"
  else
      echo "Condition is false"
  fi
  ```

---

### Loops

- `for`, `while`, `until`
- Example:
  ```bash
  for i in {1..5}; do
      echo "Number $i"
  done
  ```

---

## 7. Working with Variables

### Defining Variables

- Syntax: `variable_name="value"`
- Access: `$variable_name`
- Example:
  ```bash
  name="John"
  echo "Hello, $name"
  ```

### Special Variables

- `$0` - The name of the script.
- `$1, $2, ...` - Positional parameters.
- `$@` - All arguments.
- `$#` - Number of arguments.
- `$?` - Exit status of the last command.

---

## 8. Functions in Bash

### Defining a Function

```bash
function_name() {
    commands
}
```

### Calling a Function

```bash
function_name
```

### Example

```bash
greet() {
    echo "Hello, $1"
}
greet "World"
```

---

## 9. Advanced Bash Scripting

### Arrays

- Define: `array=(value1 value2 value3)`
- Access: `${array[index]}`
- Example:
  ```bash
  fruits=("apple" "banana" "cherry")
  echo ${fruits[1]}  # Outputs: banana
  ```

### Regular Expressions

- Use `[[ ... ]]` for pattern matching.
- Example:
  ```bash
  if [[ "abc123" =~ [0-9]+ ]]; then
      echo "Contains numbers"
  fi
  ```

### Command Substitution

- Syntax: `$(command)`
- Example:
  ```bash
  current_date=$(date)
  echo "Today is $current_date"
  ```

### Process Management

- Run in background: `command &`
- List jobs: `jobs`
- Bring to foreground: `fg`
- Send to background: `bg`

### Input/Output Redirection

- `>` - Redirect output to a file.
- `>>` - Append output to a file.
- `<` - Redirect input from a file.
- `|` - Pipe output to another command.

---

## 10. Debugging Bash Scripts

### Debugging Options

- `set -x` - Enable debugging (prints each command before execution).
- `set -e` - Exit immediately if a command fails.

### Example

```bash
#!/bin/bash
set -x
echo "Debugging this script"
```

### Using `echo` for Debugging

- Print variable values or messages to trace script execution.

---

## 11. Best Practices

- **Use Comments**: Add comments to explain your code.
  ```bash
  # This is a comment
  echo "Hello, World"
  ```
- **Use Meaningful Variable Names**: Avoid single-letter variables.
- **Handle Errors Gracefully**: Check for errors using `$?` or `if` conditions.
- **Test in a Safe Environment**: Avoid running scripts with destructive commands on production systems.
- **Use ShellCheck**: Analyze your scripts for potential issues.

---

## 12. Resources and Further Reading

- [GNU Bash Manual](https://www.gnu.org/software/bash/manual/)
- [Bash Scripting Guide](https://tldp.org/LDP/abs/html/)
- [ShellCheck](https://www.shellcheck.net/) - A tool for analyzing shell scripts.
- [Bash Cheat Sheet](https://devhints.io/bash)

---
