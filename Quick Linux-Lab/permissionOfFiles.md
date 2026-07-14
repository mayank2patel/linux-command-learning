# Permissions & Ownership of Files

How to view and change who owns a file or directory (`chown`) and who is allowed to read, write, or execute it (`chmod`).

## Creating a New File

```bash
touch example.txt
```

## Changing the Ownership of a File

The `chown` command lets us modify both the user and group ownership of a file. Ownership determines who has control over the file.

```bash
ls -l example.txt
-rw-rw-r-- 1 labex labex 0 Jul 29 15:11 example.txt
```

Breakdown of the output:

1. `-rw-rw-r--` represents the file permissions (explored more below). The first character indicates the file type (`-` for a regular file, `d` for a directory, etc.). The remaining characters represent read, write, and execute permissions for the owner, group, and others.
2. The first `labex` is the current **owner** of the file.
3. The second `labex` is the current **group** of the file. A group is a collection of users that can share permissions.
4. `0` is the file size in bytes. Since the file is empty, its size is zero.
5. `Jul 29 15:11` is the last modified date and time.
6. `example.txt` is the file name.

`root` is the administrator account on Linux systems, and it has special privileges.

```bash
sudo chown root:root example.txt
```

In this command:

- `sudo` runs the command with root privileges. `chown` requires elevated privileges because it can affect system security. Without `sudo`, you'll get a "Permission denied" error.
- `chown` is the command to change ownership.
- `root:root` specifies the new owner and group (both set to root). The syntax is `owner:group`.
- `example.txt` is the target file.

## Changing the Ownership of a Directory

The `chown` command can also change the ownership of entire directories and their contents.

```bash
mkdir -p new-dir/subdir
echo "Hello, world" > new-dir/file1.txt
echo "Another file" > new-dir/subdir/file2.txt
```

- `mkdir -p new-dir/subdir` creates `new-dir` and its `subdir` subdirectory. The `-p` option creates parent directories as needed.
- `echo "Hello, world" > new-dir/file1.txt` creates `file1.txt` and writes text into it. The `>` symbol redirects the output of `echo` into the specified file.
- `echo "Another file" > new-dir/subdir/file2.txt` similarly creates `file2.txt` inside `new-dir/subdir`.

List the contents recursively with `-R`:

```bash
ls -lR new-dir
```

```plaintext
new-dir:
total 4
-rw-rw-r-- 1 labex labex 13 Jul 29 09:15 file1.txt
drwxrwxr-x 2 labex labex 23 Jul 29 09:15 subdir

new-dir/subdir:
total 4
-rw-rw-r-- 1 labex labex 13 Jul 29 09:15 file2.txt
```

Everything is owned by `labex`. Now change ownership recursively:

```bash
sudo chown -R root:root new-dir
```

The `-R` option tells `chown` to operate **recursively**, changing the ownership of all files and subdirectories within `new-dir`. This is crucial — without `-R`, only the `new-dir` directory's ownership would change, while the files and subdirectories inside would still be owned by `labex`.

```bash
ls -lR new-dir
```

```plaintext
new-dir:
total 4
-rw-rw-r-- 1 root root 13 Jul 29 09:15 file1.txt
drwxrwxr-x 2 root root 23 Jul 29 09:15 subdir

new-dir/subdir:
total 4
-rw-rw-r-- 1 root root 13 Jul 29 09:15 file2.txt
```

## Changing the Permissions of a File

In Linux, file permissions are represented by a series of letters or numbers.

```bash
ls -l example.txt
-rw-rw-r-- 1 root root 0 Jul 29 15:11 example.txt
```

The `-rw-rw-r--` part represents the file permissions. Let's break it down:

- The first character (`-`) indicates a regular file. Other common indicators are `d` for directory and `l` for symbolic link.
- The next three characters (`rw-`) are the **owner's** permissions (read and write, but not execute).
    - `r` (read): the owner can open and read the file.
    - `w` (write): the owner can modify the file.
    - `x` (execute): the owner can run the file (if it's a program or script). A `-` means the permission is denied.
- The next three (`rw-`) are for the **group** — same meaning, but applied to members of the file's group.
- The last three (`r--`) are for **others** (everyone else).

Now, let's change these permissions using the `chmod` command (`chmod` stands for *change mode*). We'll start with **numeric notation**:

```bash
chmod 700 example.txt
```

In this command, `700` is a numeric representation of permissions:

- The first digit (`7`) represents the owner's permissions.
- The second digit (`0`) represents the group's permissions.
- The third digit (`0`) represents others' permissions.

Each digit is a number from 0 to 7, calculated by adding the values for read, write, and execute permissions:

| Value | Permission |
| --- | --- |
| `4` | Read |
| `2` | Write |
| `1` | Execute |
| `0` | No permission |

So `7` = read (4) + write (2) + execute (1) = `4+2+1`. Therefore, **700** means: Owner → read, write, execute. Group → none. Others → none.

## Changing the Permissions of a Directory

Changing permissions for directories works similarly to files. Directory permissions control who can list the directory's contents, create new files within it, and access files already in it.

```bash
mkdir ~/test-dir
chmod 700 ~/test-dir
```

```bash
ls -ld ~/test-dir
drwx------ 2 labex labex 4096 Jul 29 15:45 /home/labex/test-dir
```

The `-d` option in `ls -l` tells `ls` to list the directory itself rather than its contents. The `d` at the beginning indicates a directory. The `rwx------` shows the owner has read, write, and execute permissions, while group and others have none. For directories:

- **Read (`r`)** allows you to list the contents of the directory using `ls`.
- **Write (`w`)** allows you to create new files and subdirectories within the directory.
- **Execute (`x`)** allows you to access files and subdirectories within the directory (i.e. `cd` into it).

```bash
chmod -R 755 ~/test-dir
```

In this command:

- `-R` applies the change recursively to all files and subdirectories. It's good practice to include it when dealing with directories, in case you add files later.
- `755` breaks down as:
    - Owner (`7`): Read (4) + Write (2) + Execute (1) = 7
    - Group (`5`): Read (4) + Execute (1) = 5
    - Others (`5`): Read (4) + Execute (1) = 5

Verify the change:

```bash
ls -ld ~/test-dir
drwxr-xr-x 2 labex labex 4096 Jul 29 15:45 /home/labex/test-dir
```

## Using Symbolic Notation for Permissions

While numeric notation is concise, **symbolic notation** can be more intuitive, especially when you only want to change a single permission. It uses letters to represent the user, group, and others, plus operators to add or remove permissions.

```bash
cd ~/project
echo '#!/bin/bash' > script.sh
echo 'echo "Hello, World"' >> script.sh
```

- The first `echo` creates `script.sh` and writes `#!/bin/bash`. This first line is called a **shebang**, and it tells Linux to run the script with Bash.
- The second `echo` appends a new line with `>>`. It writes `echo "Hello, World"`, which prints `Hello, World` when the script runs.

```bash
ls -l script.sh
-rw-rw-r-- 1 labex labex 32 Jul 29 16:30 script.sh
```

Try to run it:

```bash
./script.sh
```

You'll see a "Permission denied" error because the script doesn't have execute permission yet. The `./` tells the shell to execute the script in the current directory. Add execute permission:

```bash
chmod u+x script.sh
```

In this command:

- `u` refers to the **user** (owner). Other options are `g` for group, `o` for others, and `a` for all.
- `+x` adds execute permission. The `+` symbol adds a permission, while `-` removes one.
- So `u+x` means "add execute permission for the owner."

```bash
ls -l script.sh
-rwxrw-r-- 1 labex labex 32 Jul 29 16:30 script.sh
```

The `x` now appears in the owner's permissions, so `./script.sh` will run.

## Quick Reference

| Command | What it does |
| --- | --- |
| `chown user:group file` | Change owner and group of a file. |
| `chown -R user:group dir` | Change ownership recursively. |
| `chmod 700 file` | Set numeric permissions (owner rwx, group/others none). |
| `chmod -R 755 dir` | Set numeric permissions recursively. |
| `chmod u+x file` | Add execute permission for the owner (symbolic). |
| `chmod g-w file` | Remove write permission for the group (symbolic). |

**Permission values:** read = `4`, write = `2`, execute = `1`. Add them per role (owner, group, others).
