# stdin (Standard Input)

In the previous lesson we redirected the standard **output** (`stdout`) stream. We can manage the standard **input** (`stdin`) stream in much the same way. By default a program reads its `stdin` from the keyboard, but we can also feed it a file or the output of another process.

> 🧠 **Think of it like…** choosing where a machine gets its raw material. Normally you hand-feed it from the keyboard; `<` swaps in a conveyor belt that feeds straight from a file.

**Under the hood:**

```mermaid
flowchart LR
    F["peanuts.txt"] -->|"read as stdin"| CMD["cat"] -->|"stdout"| OUT["banana.txt"]
```

## stdin and stdout

Every command-line process works with at least two data streams: standard input (`stdin`) and standard output (`stdout`). A program **reads** data from `stdin` and **writes** its results to `stdout`. Controlling both is central to effective command-line work.

## Redirecting stdin with `<`

Just as `>` redirects `stdout`, the `<` operator redirects `stdin` — it tells a command to read its input from a file instead of waiting for you to type at the keyboard.

```bash
command < inputfile
```

## Example: Copying a File Through Streams

The `peanuts.txt` file from the last lesson contains `Hello World`. Consider:

```bash
cat < peanuts.txt > banana.txt
```

Here is what happens, step by step:

- `< peanuts.txt` redirects `stdin`, so `cat` reads from the file instead of the keyboard.
- `cat` processes its input — the contents of `peanuts.txt`.
- `> banana.txt` redirects `cat`'s `stdout` into a new file, `banana.txt`.

The result: the contents of `peanuts.txt` are copied into `banana.txt`, managing both `stdin` and `stdout` in one command.

## Quick Reference

| Operator | What it does |
| --- | --- |
| `<` | Redirect `stdin` — read input from a file. |
| `>` | Redirect `stdout` — write output to a file (overwrite). |
| `command < in > out` | Read from `in`, write to `out`, in one line. |
