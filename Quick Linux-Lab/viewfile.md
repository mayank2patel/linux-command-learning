# Viewing File Contents

A quick tour of the commands used to print, peek at, and compare the contents of files: `cat`, `head`, `tail`, and `diff`.

## Print File Contents

```bash
cat /tmp/hello
```

`cat` prints the entire contents of a file to the terminal.

Add the `-n` option to number the output lines:

```bash
cat -n /tmp/hello
```

The `-n` here is called an option or a flag. It tells `cat` to number all output lines.

## Print the Top Lines of a File

```bash
head -n1 /tmp/hello
```

The `head` command, as its name suggests, is used to view the beginning or "head" of a file. Here, `-n1` tells `head` to show only the first line. The `1` can be changed to any number to show that many lines.

## View the First Few Bytes of a File

```bash
head -c1 /tmp/hello
```

The `-c1` option tells `head` to show only the first byte (character) of the file. Like with `-n`, you can change the `1` to any number to see that many bytes.

## Print the Last Lines of a File

```bash
tail -n1 /tmp/hello
```

`tail` is the opposite of `head` — it shows the end of a file. The `-n1` option tells `tail` to show only one line, in this case the last line of the file.

## View the Last Few Bytes of a File

```bash
tail -c1 /tmp/hello
```

You might not see any output. This is because the last character is likely a newline character, which is invisible. Try showing the last two bytes instead:

```bash
tail -c2 /tmp/hello
```

## Comparing Files

The `diff` command compares two files and shows the differences between them.

```bash
diff file1 file2
```

Output:

```plaintext
1c1
< this is file1
---
> this is file2
```

The `diff` command produces output that describes what changes are needed to make the first file identical to the second. It doesn't matter which file was created or modified first; `diff` only compares their contents at the time you run the command.

- `1c1`: line 1 in the first file needs to be **c**hanged to match line 1 in the second file.
- `< this is file1`: the `<` symbol indicates a line from the first file (`file1`).
- `---`: a separator between the lines from `file1` and `file2`.
- `> this is file2`: the `>` symbol indicates a line from the second file (`file2`).

In simple terms, to make `file1` match `file2`, the line "this is file1" would need to be replaced with "this is file2".

## Comparing Directories

Use `-r` (recursive) to compare two directories and every file inside them:

```bash
diff -r ~/Desktop ~/Code
```

## Quick Reference

| Command | What it does |
| --- | --- |
| `cat file` | Print the whole file. |
| `cat -n file` | Print the file with line numbers. |
| `head -n N file` | Show the first N lines. |
| `head -c N file` | Show the first N bytes. |
| `tail -n N file` | Show the last N lines. |
| `tail -c N file` | Show the last N bytes. |
| `diff a b` | Show differences between two files. |
| `diff -r dirA dirB` | Compare two directories recursively. |
