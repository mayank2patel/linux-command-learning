# Linux Command Cheatsheet

A single-page reference of every command covered in these notes — what each one does, plus the options that enhance its capabilities. For fuller explanations and examples, follow the links to the detailed notes.

**Legend:** `[ ]` = optional argument · `...` = repeatable · `SOURCE`/`DEST` = file or directory paths.

---

## Navigation & Shell

### `pwd` — print working directory
Shows the absolute path of the directory you are currently in. See [pwd.md](Command%20Line/pwd.md).

```bash
pwd
```

### `cd` — change directory
Moves the shell into another directory. See [cd.md](Command%20Line/cd.md).

```bash
cd [DIRECTORY]
```

| Shortcut | Goes to |
| --- | --- |
| `cd ~` | Home directory |
| `cd ..` | Parent directory |
| `cd -` | Previous directory |
| `cd .` | Current directory |

### `history` — command history
Lists commands you've run so you can find and reuse them. See [history.md](Command%20Line/history.md).

```bash
history
```

| Option / Shortcut | Effect |
| --- | --- |
| `!!` | Re-run the last command. |
| `!N` | Re-run command number N. |
| `!prefix` | Re-run the last command starting with `prefix`. |
| `Ctrl-R` | Reverse-search through history. |
| `-c` | Clear the in-memory history list. |
| `-w` | Write history to `~/.bash_history`. |
| `-d N` | Delete history entry number N. |

---

## Getting Help

### `man` — manual pages
Open the full manual for a command: description, options, and usage. See [man.md](Command%20Line/man.md).

```bash
man COMMAND
man 5 passwd        # read a specific numbered section
```

| Key (inside `man`) | Effect |
| --- | --- |
| `/text` | Search forward for `text`. |
| `n` / `N` | Jump to the next / previous match. |
| `q` | Quit. |

### `whatis` — one-line description
Prints the one-line summary of a command from its man page. See [whatis.md](Command%20Line/whatis.md).

```bash
whatis cat
```

### `apropos` — search descriptions
Searches man page descriptions by keyword — useful when you forget a command's name.

```bash
apropos password
```

### `help` — Bash built-in help
Shows help for Bash built-ins such as `cd`, `echo`, and `history`. See [help.md](Command%20Line/help.md).

```bash
help cd
COMMAND --help      # usage summary for most external programs
type COMMAND        # is it a built-in or an external program?
```

---

## Listing & Inspecting

### `ls` — list directory contents
Lists files and directories. See [ls.md](Command%20Line/ls.md).

```bash
ls [OPTIONS] [PATH]
```

| Option | Effect |
| --- | --- |
| `-a` | Show hidden files (dotfiles). |
| `-l` | Long format (permissions, owner, size, date). |
| `-h` | Human-readable sizes (use with `-l`). |
| `-r` | Reverse the sort order. |
| `-t` | Sort by modification time. |
| `-S` | Sort by file size. |
| `-d` | List the directory itself, not its contents. |

### `file` — identify file type
Inspects a file's contents to report what type it really is (not just its extension). See [file.md](Command%20Line/file.md).

```bash
file [OPTIONS] FILE...
```

| Option | Effect |
| --- | --- |
| `-i` | Show MIME type information. |
| `-b` | Brief mode (omit the filename). |
| `-L` | Follow symbolic links. |
| `-z` | Look inside compressed files. |

### `find` — search for files
Recursively searches directory trees by name, type, size, or time. See [find.md](Command%20Line/find.md).

```bash
find [PATH] [EXPRESSION]
```

| Option | Effect |
| --- | --- |
| `-name PATTERN` | Match by filename. |
| `-iname PATTERN` | Match by filename, case-insensitive. |
| `-type f` / `-type d` | Match files / directories. |
| `-size +10M` | Files larger than 10 MB (`-1k` = smaller than 1 KB). |
| `-mtime -7` | Modified in the last 7 days (`+30` = older than 30 days). |
| `-maxdepth N` | Limit search depth. |
| `-exec CMD {} \;` | Run a command on each match. |

---

## Viewing File Contents

### `cat` — concatenate & print
Prints whole files, joins multiple files, and (with redirection) creates files. See [cat.md](Command%20Line/cat.md).

```bash
cat [OPTIONS] FILE...
cat a b > combined      # write joined output to a new file
cat a b >> combined     # append instead of overwrite
```

| Option | Effect |
| --- | --- |
| `-n` | Number all output lines. |
| `-b` | Number only non-empty lines. |
| `-s` | Squeeze repeated blank lines into one. |
| `-A` | Show tabs, line endings, and non-printing characters. |

### `less` — page through files
Displays large files one screen at a time without flooding the terminal. See [less.md](Command%20Line/less.md).

```bash
less [OPTIONS] FILE
```

| Option / Key | Effect |
| --- | --- |
| `-N` | Show line numbers. |
| `+G` | Open at the end of the file. |
| `+F` | Follow new content (like `tail -f`). |
| `/text`, `?text` | Search forward / backward. |
| `n`, `N` | Next / previous match. |
| `g`, `G` | Jump to start / end. |
| `q` | Quit. |

### `head` — first lines of a file
Shows the beginning of a file. See [viewfile.md](Quick%20Linux-Lab/viewfile.md).

```bash
head [OPTIONS] FILE
```

| Option | Effect |
| --- | --- |
| `-n N` | Show the first N lines. |
| `-c N` | Show the first N bytes. |

### `tail` — last lines of a file
Shows the end of a file — the opposite of `head`. See [viewfile.md](Quick%20Linux-Lab/viewfile.md).

```bash
tail [OPTIONS] FILE
```

| Option | Effect |
| --- | --- |
| `-n N` | Show the last N lines. |
| `-c N` | Show the last N bytes. |
| `-f` | Follow the file as new lines are added. |

### `diff` — compare files
Reports the changes needed to make one file match another. See [viewfile.md](Quick%20Linux-Lab/viewfile.md).

```bash
diff [OPTIONS] FILE1 FILE2
```

| Option | Effect |
| --- | --- |
| `-r` | Compare directories recursively. |
| `-i` | Ignore case differences. |
| `-u` | Unified format (the style used by patches). |

---

## Creating & Managing Files

### `touch` — create files / update timestamps
Creates empty files or updates a file's access and modification times. See [touch.md](Command%20Line/touch.md).

```bash
touch [OPTIONS] FILE...
```

| Option | Effect |
| --- | --- |
| `-a` | Change only the access time. |
| `-m` | Change only the modification time. |
| `-c` | Do not create the file if it doesn't exist. |
| `-d "DATE"` | Use a specific date string. |
| `-r FILE` | Copy the timestamp from another file. |
| `-t STAMP` | Use a compact numeric timestamp. |

### `mkdir` — make directories
Creates one or more directories. See [mkdir.md](Command%20Line/mkdir.md).

```bash
mkdir [OPTIONS] DIRECTORY...
```

| Option | Effect |
| --- | --- |
| `-p` | Create parent directories as needed. |
| `-m MODE` | Set permissions on the new directory. |
| `-v` | Print a message for each directory created. |

### `cp` — copy files & directories
Copies files or directories, leaving the original in place. See [cp.md](Command%20Line/cp.md).

```bash
cp [OPTIONS] SOURCE DEST
```

| Option | Effect |
| --- | --- |
| `-r`, `-R` | Copy directories recursively. |
| `-i` | Prompt before overwriting. |
| `-f` | Force the overwrite. |
| `-n` | Never overwrite (no clobber). |
| `-p` | Preserve mode, ownership, and timestamps. |
| `-a` | Archive mode (recursive + preserve everything). |
| `-u` | Copy only when the source is newer. |
| `-v` | Verbose — show each file copied. |

### `mv` — move & rename
Moves files/directories to a new location or renames them. See [mv.md](Command%20Line/mv.md).

```bash
mv [OPTIONS] SOURCE DEST
```

| Option | Effect |
| --- | --- |
| `-i` | Prompt before overwriting. |
| `-n` | Never overwrite (no clobber). |
| `-b` | Back up the destination before overwriting. |
| `-v` | Verbose — show each move. |
| `-t DIR` | Specify the target directory first. |

### `rm` / `rmdir` — remove files & directories
Deletes files and directories. Command-line deletion is usually permanent — there is no trash. See [rm.md](Command%20Line/rm.md).

```bash
rm [OPTIONS] FILE...
rmdir DIRECTORY      # only removes empty directories
```

| Option | Effect |
| --- | --- |
| `-i` | Prompt before every removal. |
| `-I` | Prompt once before removing many files / recursively. |
| `-f` | Force; ignore nonexistent files, no prompts. |
| `-r`, `-R` | Remove directories and their contents recursively. |
| `-v` | Verbose — show what was removed. |

> ⚠️ **`rm -rf` deletes a whole tree with no confirmation.** Before running it, check `pwd`, preview wildcards with `ls`, and watch for accidental spaces in the path.

---

## Permissions & Ownership

See the full walkthrough in [permissionOfFiles.md](Quick%20Linux-Lab/permissionOfFiles.md).

### `chmod` — change permissions
Sets who can read (`4`), write (`2`), and execute (`1`) a file, for the owner, group, and others.

```bash
chmod 700 file          # numeric: owner rwx, group none, others none
chmod -R 755 dir        # recursive
chmod u+x script.sh     # symbolic: add execute for the owner
```

| Notation | Meaning |
| --- | --- |
| `-R` | Apply recursively. |
| `4` / `2` / `1` | Read / write / execute values (add them per role). |
| `u` / `g` / `o` / `a` | user (owner) / group / others / all. |
| `+` / `-` / `=` | Add / remove / set exactly. |

### `chown` — change ownership
Changes the user and/or group that owns a file or directory.

```bash
chown user:group file
chown -R user:group dir      # recursive
```

| Option | Effect |
| --- | --- |
| `-R` | Change ownership recursively. |
| `owner:group` | Set both owner and group (either part is optional). |

---

## User Account Management

Requires `sudo`. See the full walkthrough in [uam.md](Quick%20Linux-Lab/uam.md).

| Command | What it does |
| --- | --- |
| `useradd NAME` | Create a new user account. |
| `useradd -m NAME` | Create a user **with** a home directory. |
| `passwd NAME` | Set or change a user's password. |
| `passwd -l NAME` | Lock (disable) an account. |
| `passwd -u NAME` | Unlock an account. |
| `usermod -d DIR NAME` | Change a user's home directory. |
| `usermod -s SHELL NAME` | Change a user's default shell. |
| `usermod -aG GROUP NAME` | Add a user to a group (append, keep existing groups). |
| `userdel -r NAME` | Delete a user and their home directory. |
| `groups NAME` | List the groups a user belongs to. |
| `su - NAME` | Switch to another user account. |

**Where things live:** account records → `/etc/passwd` · encrypted passwords → `/etc/shadow`.

---

## System Info

Quick reconnaissance of who you are and what the machine is doing. See the [System Reconnaissance lab](Quick%20Linux-Lab/TheLayofLand.md).

### `whoami` — current user
Prints the username you are currently acting as.

```bash
whoami
```

### `id` — user & group IDs
Shows your UID, primary GID, and every group you belong to.

```bash
id
id -u        # numeric user ID only
id -nG       # group names only
```

### `uname` — system information
Reports kernel and system details.

```bash
uname        # kernel name
uname -a     # everything on one line
```

| Option | Effect |
| --- | --- |
| `-a` | All information. |
| `-s` | Kernel name (the default). |
| `-r` | Kernel release. |
| `-m` | Hardware architecture. |
| `-n` | Network (host) name. |

### `uptime` — how long the system has run
Shows the time, uptime, logged-in users, and load averages (1, 5, 15 min).

```bash
uptime
uptime -p        # pretty, human-readable form
```

### `top` — live process monitor
Interactive, auto-refreshing view of CPU, memory, and processes. Press `q` to quit.

```bash
top
```

| Key (inside `top`) | Effect |
| --- | --- |
| `q` | Quit. |
| `P` | Sort by CPU usage. |
| `M` | Sort by memory usage. |
| `k` | Kill a process by PID. |

---

## Streams & Redirection

Control where a command's input comes from and where its output (and errors) go. See the [Text-Fu notes](Text-Fu/stfout.md) for full walkthroughs. Each stream has a numeric **file descriptor**: `0` = stdin, `1` = stdout, `2` = stderr.

| Operator | What it does |
| --- | --- |
| `command > file` | Redirect `stdout` to a file (overwrite). |
| `command >> file` | Redirect `stdout` to a file (append). |
| `command < file` | Redirect `stdin` — read input from a file. |
| `a \| b` | Pipe: send `a`'s `stdout` into `b`'s `stdin`. |
| `command \| tee file` | Show output **and** save it to a file at once. |
| `command 2> file` | Redirect `stderr` (errors) to a file. |
| `command 2>&1` | Send `stderr` wherever `stdout` currently points. |
| `command &> file` | Redirect both `stdout` and `stderr` to a file. |
| `command 2> /dev/null` | Discard error messages. |

---

## Handy Shell Extras

| Feature | What it does |
| --- | --- |
| `*` | Wildcard: match any sequence of characters. |
| `?` | Wildcard: match any single character. |
| `[abc]` | Wildcard: match any one of the enclosed characters. |
| `Tab` | Auto-complete commands, filenames, and paths. |
| `Ctrl-C` | Cancel the current command. |
| `clear` | Clear the terminal screen. |
