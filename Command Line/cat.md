# cat (Concatenate)

After learning to navigate the filesystem, the next step is to view the contents of files. A fundamental and versatile tool for this is the `cat` command. The name `cat` is short for **"concatenate,"** which hints at its ability to link files together.

## Viewing File contents

The most basic use of the cat command is to display the content of a single file directly in your terminal.

```bash
cat myfile.txt
```

This command will print the entire content of myfile.txt to the screen. While this is perfect for short configuration files or text snippets, it's not ideal for viewing large files, as the text will scroll by very quickly. We will cover tools better suited for large files in a later lesson.

## Concatenating files

True to its name, cat can combine, or concatenate, multiple files and display their combined output. It reads the files in the order they are provided and prints them sequentially.

```bash
cat dogfile birdfile
```

This command will first display the contents of `dogfile`, immediately followed by the contents of `birdfile`.

To save the combined output into a new file, use redirection:

```bash 
cat dogfile birdfile > animals
```

## Creating Files with Redirection

You can also use cat with the output redirection operator (>) to create new files. This is a quick way to write text into a file directly from your terminal.

```bash 
cat > newfile.txt 
```

After running this command, you can type your text. Press Ctrl+D on a new line to save and exit. This will create newfile.txt with the text you entered. Be careful, as using `>` on an existing file will overwrite it completely.

To append to a file instead of overwriting it, use `>>`.

```bash
cat >> notes.txt
```

### Why use cat to write?

The secret is that the `cat` command isn't actually writing to the file at all — your terminal shell is. To understand how this works, it helps to look at the two separate pieces in play: how `cat` handles data streams, and what the redirection operator (`>`) does behind the scenes.

**1. What cat actually does (Standard Input & Output)**

At its fundamental level, `cat` is a simple data pipeline: it takes text from an input and pushes it out to Standard Output (your terminal screen).

- When you give it a filename (e.g. `cat myfile.txt`), it reads data from that file and pushes it to your screen.
- When you give it **no** filename (just typing `cat` by itself and pressing Enter), it defaults to reading from Standard Input (your keyboard). Every time you type a line and hit Enter, `cat` immediately echoes that exact line back to your screen.

**2. What the redirection operator (`>`) does**

The `>` symbol is a feature of your terminal shell (like Bash or Zsh), completely independent of `cat`. Think of `>` as a railroad switch for data. Whenever you put `>` after any command, the shell steps in and says: *"I am going to catch whatever text this command normally sends to the screen, and divert it into this file instead."*

## Common cat Options

The `cat` command has several options to modify its behavior.

| Option | Description |
| --- | --- |
| `-n` | Number all output lines, starting from 1. |
| `-b` | Number only non-empty output lines. |
| `-s` | Squeeze multiple blank lines into one blank line. |
| `-A` | Show non-printing characters, tabs, and line endings. |

## Common Questions

1. **Can `cat` edit a file?** Not interactively. It can create or overwrite files with redirection, but a text editor is better for editing.
2. **What is the difference between `>` and `>>`?** `>` overwrites a file. `>>` appends to the end of a file.
