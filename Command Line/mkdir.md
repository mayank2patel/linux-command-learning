# mkdir (Make Directory)

As you work with files, you will need to organize them into directories. The primary tool for this task is the `mkdir` command, which stands for *make directory*.

```bash
mkdir [OPTIONS] DIRECTORY...
```

> 🧠 **Think of it like…** putting a fresh, empty folder into the filing cabinet.

**Under the hood:**

```mermaid
flowchart LR
    A["mkdir dir"] --> B["create directory entry"] --> C["empty folder ready"]
```

## Creating a Single Directory

The most basic use of `mkdir` is to create a single new directory. If the directory does not already exist, this command creates it in your current location.

```bash
mkdir documents
```

## Creating Multiple Directories

You can also create several directories at once by listing their names, separated by spaces. This is an efficient way to set up multiple folders quickly.

```bash
mkdir books paintings
```

## Creating Nested Directories

Sometimes you need to create a directory and its parent directories simultaneously. The `-p` option is perfect for this. It prevents errors if parent directories do not exist.

```bash
mkdir -p books/hemingway/favorites
```

This single command creates `books`, `hemingway`, and `favorites` if they do not already exist.

## Setting Directory Permissions

Use `-m` to set permissions while creating a directory.

```bash
mkdir -m 755 public
```

You will learn more about permissions later, but this example creates a directory that the owner can write to and others can read and enter.

## Common mkdir Options

| Option | Description |
| --- | --- |
| `-p` | Create parent directories as needed. |
| `-m MODE` | Set permissions for the new directory. |
| `-v` | Print a message for each created directory (verbose). |

Example with verbose output:

```bash
mkdir -pv projects/app/src
mkdir: created directory 'projects'
mkdir: created directory 'projects/app'
mkdir: created directory 'projects/app/src'
```

## Common Questions

1. **Why does `mkdir` say "File exists"?** A file or directory with that name already exists. Use `ls` to inspect it.
2. **How do I create nested directories?** Use `mkdir -p parent/child/grandchild`.
3. **Can `mkdir` create files?** No. Use `touch` to create empty files.
