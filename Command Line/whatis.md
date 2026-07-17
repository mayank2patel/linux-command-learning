# whatis (One-Line Description)

As you explore the command line you will meet a huge number of commands, and it is natural to forget what a specific one does. The `whatis` command gives you a quick reminder without opening the full manual.

> 🧠 **Think of it like…** the one-sentence blurb on the back of a book — just enough to remember what it's for.

**Under the hood:**

```mermaid
flowchart LR
    A["whatis cat"] --> B["read the man page NAME line"] --> C["print one-line summary"]
```

## What `whatis` Does

`whatis` displays a concise, one-line description of a command, taken from its manual page. It is the quickest way to jog your memory about a command's primary purpose.

## Using `whatis`

Type `whatis` followed by the command you want to look up:

```bash
whatis cat
```

```plaintext
cat (1)              - concatenate files and print on the standard output
```

## Understanding the Output

The description comes from the **NAME** section of the command's man page. The number in parentheses is the manual section the entry belongs to. If a name has pages in several sections, `whatis` shows a line for each:

```bash
whatis passwd
```

```plaintext
passwd (1)           - change user password
passwd (5)           - the password file
```

## whatis vs. man vs. apropos

| Command | What it gives you |
| --- | --- |
| `whatis ls` | A one-line description for an exact command name. |
| `man ls` | The full manual page. |
| `apropos KEYWORD` | Every man page whose description matches a keyword. |

Use `apropos` when you only remember roughly what you want to do:

```bash
apropos password
```

## Common Questions

1. **Why does `whatis` say "nothing appropriate"?** The command may have no man page installed, or the man database may need rebuilding (`sudo mandb`).
2. **Does `whatis` show command options?** No. Use `man COMMAND` or `COMMAND --help` for options.
3. **Is `whatis` the same as `which`?** No. `whatis` describes a command; `which` shows the path to its executable.
