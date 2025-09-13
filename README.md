# Minishell

A minimal shell implementation written in C as part of the 42 School curriculum. This project recreates the functionality of bash, including command parsing, execution, built-in commands, and pipeline handling.

## Features

### Built-in Commands
- `cd` - Change directory
- `pwd` - Print working directory
- `echo` - Print arguments with options
- `env` - Display environment variables
- `export` - Set environment variables
- `unset` - Unset environment variables
- `exit` - Exit the shell

### Advanced Features
- **Pipeline Support** - Execute multiple commands with pipes (`|`)
- **Redirection** - Input/output redirection (`<`, `>`, `>>`)
- **Here Document** - Handle `<<` redirection
- **Environment Variables** - Full environment variable management
- **Signal Handling** - Proper handling of SIGINT, SIGQUIT, and other signals
- **Quote Handling** - Support for single and double quotes
- **Command History** - Using readline library for command history

## Project Structure

```
minishell/
├── includes/
│   ├── libft.h          # Libft library header
│   └── minishell.h      # Main project header
├── Libft/               # Custom C library (42's libft)
├── srcs/
│   ├── builtin/         # Built-in command implementations
│   ├── execute/         # Command execution logic
│   ├── free/            # Memory management
│   ├── main/            # Main program entry point
│   ├── parse/           # Command parsing and tokenization
│   ├── signal/          # Signal handling
│   └── utility/         # Utility functions
├── Makefile
└── README.md
```

## Installation

### Prerequisites
- GCC compiler
- Make
- Readline library (for command history and line editing)

### Rewriting
Rewrite your gnu readline library path in the Makefile
+ common path -> `/usr/local/lib`, `/usr/local/include`
+ if you can't find readline library, `yum install readline-devel`
```
READ_INC_FG = -I/usr/include/readline
READ_LIB_FG = -L/usr/include/readline
```

### Building
```bash
make
```

### Cleaning
```bash
make clean      # Remove object files
make fclean     # Remove object files and executable
make re         # Clean and rebuild
```

## Usage

```bash
./minishell
```

Once running, you can use the shell like any other Unix shell:

```bash
Minishell > ls -la
Minishell > echo "Hello World"
Minishell > cd /path/to/directory
Minishell > export MY_VAR="value"
Minishell > env | grep MY_VAR
Minishell > ls | grep .c | wc -l
Minishell > cat < input.txt > output.txt
Minishell > exit
```

## Key Components

### Parsing
- Tokenizes input into commands and arguments
- Handles quotes (single and double) properly
- Supports environment variable expansion
- Validates syntax for pipes and redirections

### Execution
- Fork-based process execution
- Pipeline implementation with proper file descriptor management
- Built-in command detection and execution
- External command execution via `execve`

### Memory Management
- Careful memory allocation and deallocation
- Prevention of memory leaks
- Proper cleanup of resources

### Signal Handling
- Handles Ctrl+C (SIGINT) and Ctrl+\ (SIGQUIT)
- Different behavior for main process vs child processes
- Proper signal handling during pipeline execution

## Technical Details

- **Language**: C
- **Standards**: C99
- **Libraries**: libft (custom), readline
- **Architecture**: Unix-like shell implementation
- **Memory Management**: Manual memory management with malloc/free

## Error Handling

The shell provides comprehensive error handling for:
- Invalid syntax
- Command not found
- Permission denied
- File not found
- Memory allocation failures
- Signal interruptions

## Limitations

This is a minimal shell implementation and does not include:
- Advanced scripting features
- Job control
- Advanced globbing patterns
- Some advanced redirection features

## Authors

This project was developed as part of the 42 School curriculum by:
- hyeonkki
- kyunkim

## License

This project is part of the 42 School curriculum and follows the school's guidelines and restrictions.