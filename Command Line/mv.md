# mv (Move)

The `mv` command, short for *move*, is a fundamental utility in any Linux environment. It serves two primary purposes: **renaming** files or directories and **moving** them to a different location.

```bash
mv [OPTIONS] SOURCE DESTINATION
```

Unlike `cp`, which creates a copy, `mv` changes where the original item lives or what it is called.

> 🧠 **Think of it like…** moving a book to a new shelf — same book, new spot, nothing left behind. Renaming is just "moving" it to the same shelf under a new title.

**Under the hood:**

```mermaid
flowchart LR
    A["SOURCE"] --> B["relink to new path"] --> C["DEST — original gone"]
```

## Renaming Files and Directories

One of the most common uses of `mv` is renaming. The syntax is straightforward: specify the old name and the new name.

To rename a file:

```bash
mv oldfile newfile
```

This same logic applies to renaming directories:

```bash
mv old_directory_name new_directory_name
```

## Moving Files and Directories

The other core function of `mv` is to move items from one location to another.

To move a single file into a different directory:

```bash
mv file2 /home/pete/Documents
```

You can also move multiple files at once. Simply list all the source files followed by the target directory:

```bash
mv file_1 file_2 somedirectory/
```

On GNU/Linux systems, a useful option is `-t`, which lets you specify the target directory first. This can be clearer when moving many files.

```bash
mv -t somedirectory/ file_1 file_2
```

Unlike the `cp` command, you do **not** need a recursive option to move a directory. `mv` handles directories by default.

## Important Options for the mv Command

By default, if you move a file to a destination where a file with the same name already exists, `mv` will overwrite it without warning. To prevent accidental data loss, use the following options:

`-i` (interactive) prompts you for confirmation before overwriting any existing file.

```bash
mv -i source_file destination_directory
```

`-b` (backup) creates a backup of the destination file before overwriting it. The backup is typically renamed with a tilde (`~`) suffix.

```bash
mv -b file1 directory_with_file1
```

`-v` (verbose) makes `mv` print out what it is doing, showing each file being moved or renamed.

```bash
mv -v file1 file2 somedirectory/
```

`-n` (no clobber) prevents overwriting an existing destination file.

```bash
mv -n source_file destination_directory
```

## Common mv Examples

Rename a file:

```bash
mv draft.txt final.txt
```

Move a directory:

```bash
mv project /home/pete/Documents/
```

Move all text files into a folder:

```bash
mv *.txt notes/
```

> **Tip:** Preview wildcard matches with `ls` before moving many files.

## Common mv Options

| Option | Description |
| --- | --- |
| `-i` | Prompt before overwriting (interactive). |
| `-n` | Never overwrite an existing file (no clobber). |
| `-b` | Back up the destination file before overwriting. |
| `-v` | Show each file as it is moved (verbose). |
| `-t DIR` | Specify the target directory first. |

## Common Questions

1. **Does `mv` copy files?** No. `mv` moves or renames the original item.
2. **Can `mv` overwrite files?** Yes. Use `mv -i` to ask first or `mv -n` to avoid overwriting.
3. **Do I need `mv -r` for directories?** No. `mv` moves directories without `-r`.
