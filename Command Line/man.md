# man (Manual Pages)

In Linux, nearly every command comes with its own instruction manual. These are called **man pages** (short for "manual pages"), and they are an essential resource for learning the system.

> 🧠 **Think of it like…** the thick instruction manual that comes in the box: everything is in there, so you search for the part you need.

**Under the hood:**

```mermaid
flowchart LR
    A["man ls"] --> B["find the man page"] --> C["open in a pager"] --> D["scroll / search / quit"]
```

## Understanding Man Pages

Man pages are the built-in documentation for commands, utilities, and system calls. They describe what a command does, its available options, and how to use it — making them your first and best source for command-line help.

## Reading a Manual

To view the manual for any command, run `man` followed by the command name:

```bash
man ls
```

This opens the `ls` man page. Scroll with the arrow keys, search with `/`, and press `q` to quit.

## Finding Details on Options

Man pages are especially useful for understanding options. If you have seen `ls -l` and want to know what `-l` means, open the page and search for it:

```bash
man ls
```

Once inside the page, these keys move you around:

| Key | Action |
| --- | --- |
| `/term` | Search forward for `term`. |
| `n` | Jump to the next match. |
| `N` | Jump to the previous match. |
| `q` | Quit the man page. |

## Manual Sections

Manual pages are organized into numbered sections:

| Section | Contents |
| --- | --- |
| `1` | User commands. |
| `2` | System calls. |
| `3` | Library functions. |
| `5` | File formats. |
| `8` | System administration commands. |

Sometimes the same name exists in more than one section. Give the section number to choose which one you want:

```bash
man 5 passwd
man 1 passwd
```

Here `man 5 passwd` describes the password *file*, while `man 1 passwd` describes the password *command*.

## Common Questions

1. **Why is `man` output so long?** Man pages are complete reference documentation. Use `/` to search straight to the part you need.
2. **How do I quit `man`?** Press `q`.
3. **What if no man page exists?** Try `COMMAND --help`, `help COMMAND`, or install your distribution's documentation package.
