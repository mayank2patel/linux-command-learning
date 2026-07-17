# 🐧 Learning Linux

Personal notes on the Linux command line — written while learning, organized so they're easy to come back to. Each command has its own page with explanations, examples, and the options that make it more powerful.

> 📄 **In a hurry?** Read the [**Command Cheatsheet**](CHEATSHEET.md) for a single-page reference of every command and its key options.
>
> 🗺️ **Want the big picture?** See the [**Mind Map**](MINDMAP.md) — every command and concept in one tree.

## 📚 Contents

### Command Line
Core commands for navigating the shell and working with files and directories.

| Command | Description |
| --- | --- |
| [The Shell](Command%20Line/theShell.md) | What the shell is and how to interact with Bash. |
| [`pwd`](Command%20Line/pwd.md) | Print the current working directory. |
| [`cd`](Command%20Line/cd.md) | Change directory; absolute vs. relative paths. |
| [`ls`](Command%20Line/ls.md) | List directory contents. |
| [`cat`](Command%20Line/cat.md) | Print, concatenate, and create files. |
| [`less`](Command%20Line/less.md) | Page through large files. |
| [`touch`](Command%20Line/touch.md) | Create files and update timestamps. |
| [`mkdir`](Command%20Line/mkdir.md) | Make directories. |
| [`cp`](Command%20Line/cp.md) | Copy files and directories. |
| [`mv`](Command%20Line/mv.md) | Move and rename. |
| [`rm`](Command%20Line/rm.md) | Remove files and directories. |
| [`file`](Command%20Line/file.md) | Identify a file's real type. |
| [`find`](Command%20Line/find.md) | Search for files across directory trees. |
| [`history`](Command%20Line/history.md) | Review and reuse past commands. |
| [`man`](Command%20Line/man.md) | Read a command's full manual page. |
| [`whatis`](Command%20Line/whatis.md) | Show a one-line description of a command. |
| [`help`](Command%20Line/help.md) | Get built-in help for Bash commands. |

### Quick Linux-Lab
Short hands-on labs on file management and system administration.

| Topic | Description |
| --- | --- |
| [Viewing File Contents](Quick%20Linux-Lab/viewfile.md) | `cat`, `head`, `tail`, and `diff`. |
| [Permissions & Ownership](Quick%20Linux-Lab/permissionOfFiles.md) | `chmod` and `chown`, numeric and symbolic notation. |
| [User Account Management](Quick%20Linux-Lab/uam.md) | Create, modify, lock, and delete users. |
| [The Lay of the Land](Quick%20Linux-Lab/TheLayofLand.md) | System recon with `whoami`, `uname`, `uptime`, `id`, and `top`. |

### Text-Fu
Working with text streams and output redirection on the command line.

| Topic | Description |
| --- | --- |
| [Standard Output (`stdout`)](Text-Fu/stfout.md) | Redirecting command output with `>` and `>>`. |
| [Standard Input (`stdin`)](Text-Fu/stdin.md) | Feeding input from a file with `<`. |
| [Standard Error (`stderr`)](Text-Fu/stderr.md) | Handling errors with `2>`, `2>&1`, and `/dev/null`. |
| [Pipe & Tee](Text-Fu/pipeAndtee.md) | Chaining commands with pipes and splitting output with `tee`. |

## 🗺️ How this repo is organized

```text
.
├── Command Line/       # One page per core command
├── Quick Linux-Lab/    # Hands-on lab walkthroughs
├── Text-Fu/            # Text streams, redirection & pipes
├── CHEATSHEET.md       # Single-page quick reference of all commands
└── README.md           # You are here
```

---

*These are learning notes and are updated as I go. Corrections and suggestions are welcome.*
