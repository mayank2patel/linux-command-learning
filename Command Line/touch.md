# touch

The touch command is a standard utility on Unix-like operating systems. While its primary purpose is to change `file timestamps`, it is also commonly used to create new, empty files.

```bash
touch [OPTIONS] FILE...
```

## Creating New files

The simplest way to create an empty file is to use touch followed by a filename. If the file does not exist, touch creates it.

```bash
touch mysuperduperfile
```

After running this command, a new empty file named mysuperduperfile will appear in your current directory. You can create multiple files at once by listing their names.

```bash
touch file1.txt file2.txt file3.log
```

## **Updating File Timestamps**

The original function of touch is to **update the access and modification timestamps of a file or directory**. If you use touch on an existing file, it updates its timestamps to the current time.

You can verify this by using ls -l to check a file's timestamp, running touch on it, and then checking again.

```bash
# Check the original timestamp
ls -l mysuperduperfile

# Update the timestamp
touch mysuperduperfile

# Check the new timestamp
ls -l mysuperduperfile
```

## **Advanced Timestamp Control**

The touch command also provides options for more precise timestamp manipulation. 

Use a reference file with `-r` to copy timestamps from one file to another.

```bash
touch -r file1.txt file2.txt
```

Set a specific date and time with `-d` :

```bash
touch -d "2026-06-23 12:30:00" mysuperduperfile
```

Use `-c` when you want to update a file only if it already exists. With `-c`, touch will not create a missing file.

```bash
touch -c existing-file.txt
```

## Common touch Options

| Option | Description |
| --- | --- |
| `-a` | Change only the access time. |
| `-m` | Change only the modification time. |
| `-c` | Do not create the file if it does not exist. |
| `-d "DATE"` | Use a specific date string. |
| `-r FILE` | Use another file's timestamp as a reference. |
| `-t STAMP` | Use a timestamp in a compact numeric format. |
