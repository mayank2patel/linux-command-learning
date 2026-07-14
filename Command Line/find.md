# find

With countless files on a system, it can be challenging to locate a specific one. The `find` command searches directory trees using criteria such as name, type, size, and modification time.

```bash
find [PATH] [EXPRESSION]
```

You specify the directory to search in and the criteria for what you are looking for. For example, to search for a file named `puppies.jpg` within the `/home` directory and all its subdirectories:

```bash
find /home -name puppies.jpg
```

Searches are recursive by default, so `find /home` looks inside `/home` and its subdirectories.

## Searching by Name and Type

One of the most common uses of `find` is searching by filename. The `-name` option matches names exactly or by shell-style patterns.

```bash
find . -name "*.txt"
```

You can also specify the type of item you are searching for with the `-type` option. For instance, to find a directory instead of a file, use `d`.

```bash
find /home -type d -name MyFolder
```

Here we set the type to `d` for directory and search for an item named `MyFolder`. To search specifically for regular files, use `-type f`.

## Searching by Size and Time

You can search by file size:

```bash
find . -type f -size +10M
find . -type f -size -1k
```

The first command finds files larger than 10 megabytes. The second finds files smaller than 1 kilobyte.

You can also search by modification time:

```bash
find . -type f -mtime -7
find . -type f -mtime +30
```

`-mtime -7` means modified within the last 7 days. `-mtime +30` means modified more than 30 days ago.

## Running Actions on Results

By default, `find` prints matching paths. You can add actions such as `-print`, `-delete`, or `-exec`.

Print matches explicitly:

```bash
find . -name "*.log" -print
```

Run `ls -l` on each match:

```bash
find . -name "*.log" -exec ls -l {} \;
```

The `{}` placeholder is replaced by each matching path. The escaped semicolon `\;` marks the end of the command.

> **Be careful with destructive actions such as `-delete`.** First run the same search without `-delete` to confirm the matches.

## Common find Options

| Option | Description |
| --- | --- |
| `-name PATTERN` | Match by filename. |
| `-iname PATTERN` | Match by filename, ignoring case. |
| `-type f` | Match regular files. |
| `-type d` | Match directories. |
| `-size +10M` | Match files larger than 10 megabytes. |
| `-mtime -7` | Match files modified within the last 7 days. |
| `-maxdepth N` | Limit how deep `find` searches. |
| `-exec CMD {} \;` | Run a command on each match. |

## Common Questions

1. **Why does `find` show "Permission denied"?** Your user cannot read some directories. Search a narrower path or use appropriate privileges.
2. **Why should I quote patterns like `"*.txt"`?** Quoting prevents the shell from expanding the wildcard before `find` receives it.
3. **Is `find` recursive?** Yes. It searches subdirectories by default.
