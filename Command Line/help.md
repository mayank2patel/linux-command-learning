# help (Command Help)

When working on the command line, you will often need a quick reminder of how a command works or what options it accepts. Linux provides several help tools directly in the terminal, and `help` is the one built into Bash itself.

> 🧠 **Think of it like…** the little "how to use me" note built into a tool itself — but only for the tools baked into the shell.

**Under the hood:**

```mermaid
flowchart LR
    A["help cd"] --> B["shell built-in docs"] --> C["usage summary printed"]
```

## The `help` Command for Bash Built-ins

The `help` command is built directly into the Bash shell, and it provides information about other Bash **built-in** commands. A built-in is part of the shell itself, not a separate program — examples include `echo`, `cd`, and `pwd`.

To use it, type `help` followed by the name of the built-in:

```bash
help echo
```

This displays a summary of `echo`, its syntax, and the options it accepts. It is the fastest way to get assistance for shell-specific functions.

## The `--help` Flag for Programs

For most executable programs that are *not* built into the shell, `help` won't work. Instead, a common convention is a `--help` flag, which tells the program to print a usage summary and exit.

```bash
ls --help
```

Most programs follow this convention, but it is not universal. Trying `--help` is usually a good first step with an unfamiliar command.

## Is It a Built-in or a Program?

If you are not sure whether a command is a Bash built-in or an external program, use `type`:

```bash
type cd
type ls
```

```plaintext
cd is a shell builtin
ls is /usr/bin/ls
```

This tells you whether to reach for `help cd`, `ls --help`, or `man ls`.

## Choosing the Right Help Tool

| Tool | Use it for |
| --- | --- |
| `help COMMAND` | Bash built-ins such as `cd`, `echo`, and `history`. |
| `COMMAND --help` | A quick usage summary from many external programs. |
| `man COMMAND` | The full, detailed manual page. |
| `whatis COMMAND` | A one-line description of what a command does. |

## Common Questions

1. **Why does `help ls` not work?** `ls` is usually an external program, not a Bash built-in. Try `ls --help` or `man ls`.
2. **Why does `--help` not work for every command?** It is a widely followed convention, not a strict rule.
3. **What is the fastest way to check a command?** Use `help COMMAND` for built-ins and `COMMAND --help` for external programs.
