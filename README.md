# Angel - Linux Shell in C

## Introduction

Angel is an implementation of a Linux shell written in C language.

## Running the Shell

1. Compile the shell by running the command: `make`.
2. Start the shell by running: `./angel`. This will provide a prompt in the form `<username@system_name:path>`.
3. Enter commands at the prompt to execute them.
4. To exit the shell, run the command: `exit`.

## Features

### Built-in Commands

Angel shell provides the following built-in commands:

1. `pwd`
    - Displays the current working directory.
    - Implemented in [pwd.c](pwd.c).
    - Function Declarations in [pwd.h](pwd.h).

2. `ls [-l -a] [directory]`
    - Lists files and directories in alphabetical order.
    - Supports variations such as `ls, ls . , ls .., ls ~, ls -la / ls -al`.
    - Handles multiple directories as arguments.
    - Implemented in [ls.c](ls.c).
    - Function Declarations in [ls.h](ls.h).

3. `cd [directory]`
    - Changes the current directory.
    - Supports variations like `cd ., cd .. , cd -, cd ~`.
    - Implemented in [cd.c](cd.c).
    - Function Declarations in [cd.h](cd.h).

4. `echo [arguments]`
    - Displays specified text, handles tabs and spaces.
    - Implemented in [echo.c](echo.c).
    - Function Declarations in [echo.h](echo.h).

5. `exit`
    - Exits the shell.

6. Prompt Styling
    - Displays the prompt in blue, green, and white colors.
    - Implemented in [prompt.c](prompt.c).
    - Function Declarations in [prompt.h](prompt.h).

7. `repeat`
    - Executes a given instruction multiple times.
    - Implemented in [repeat.c](repeat.c).
    - Function Declarations in [repeat.h](repeat.h).

8. Command Handler
    - Executes various user-entered commands.
    - Implemented in [run.c](run.c).
    - Function Declarations in [run.h](run.h).

9. `headers.c`
    - Contains common headers and libraries.
    - Implemented in [headers.h](headers.h).

10. Signal Handlers
    - Monitors suspended or exited background processes.
    - Handles Ctrl+C and Ctrl+Z signals.
    - Implemented in [signalHandlers.h](signalHandlers.h).

11. `bg [JobIndex]`
    - Resumes a stopped background job.
    - Implemented in [bg.h](bg.h) and [bg.c](bg.c).

12. `fg [JobIndex]`
    - Brings a background job to the foreground.
    - Implemented in [fg.h](fg.h) and [fg.c](fg.c).

13. `sig [JobIndex] [SIGNAL]`
    - Sends a signal to a running job.
    - Implemented in [sig.h](sig.h) and [sig.c](sig.c).

14. `jobs [-r -s]`
    - Lists running or stopped background processes.
    - Implemented in [jobs.h](jobs.h) and [jobs.c](jobs.c).

15. `pipe.c`
    - Implements command pipelines using pipes.
    - Handles multiple commands sequentially.
    - Implemented in [pipe.c](pipe.c).

16. `redirection.c`
    - Implements input/output redirection.
    - Supports `<`, `>`, and `>>` operators.
    - Implemented in [redirection.c](redirection.c).

17. CTRL-Z, CTRL-C, CTRL-D
    - CTRL-Z: Stops a running foreground job.
    - CTRL-C: Interrupts a running foreground job.
    - CTRL-D: Logs out of the shell.
    - Implemented in [sig.h](sig.h), [sig.c](sig.c), and [main.c](main.c).

18. `replay -command <cmd> -interval <interval> -period <period>`
    - Executes a command at intervals for a period.
    - Implemented in [replay.c](replay.c) and [replay.h](replay.h).

19. `baywatch [-n] <interval> dirty`
    - Prints dirty memory size periodically.
    - Implemented in [dirty.c](dirty.c) and [dirty.h](dirty.h).

20. `makefile`
    - Compiles and runs the shell.
    - To compile: `make`
    - To start: `./angel`

### Foreground and Background Processes

- Displays PID and exit status of terminated background processes.
- Handles foreground processes with `&` and displays `[PID]`.
- Implemented in [foregroundProcess.c](foregroundProcess.c) and [backgroundProcess.c](backgroundProcess.c).
- Function Declarations in [foregroundProcess.h](foregroundProcess.h) and [backgroundProcess.h](backgroundProcess.h).

### Additional Commands

1. `pinfo [PID]`
    - Displays details about a process.
    - Implemented in [pinfo.c](pinfo.c).
    - Function Declarations in [pinfo.h](pinfo.h).

2. `history [num] or history`
    - Lists the last [num] commands, up to 10 by default.
    - Retains history upon shell exit in [angelHistory.txt](angelHistory.txt).
    - Implemented in [history.c](history.c).
    - Function Declarations in [history.h](history.h).

### Coding Style

- Modular code with separate `.c` files for each command.
- `main.c` coordinates different commands.
- `.h` files include necessary headers and global variables.
