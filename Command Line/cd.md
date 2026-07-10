# cd (Change directory)

To move around the Linux filesystem, you use paths to specify your destination.\
The primary tool for this is the cd command, short for change directory. It changes the shell's current working directory.

```bash
cd [DIRECTORY]
```

## Understanding Paths

There are two ways to specify a path: absolute and relative.

- Absolute path: The full path starting from the root directory (/). For example: /home/pete/Desktop.

- Relative path: A path based on your current location. If you are in /home/pete/Documents and want to access a subdirectory named taxes, you can use taxes/.

## Essential Navigation Shortcuts

Navigating with full paths can be tedious. Fortunately, the shell provides several shortcuts to make moving around much faster.\

- . (current directory): Represents the directory you are currently in.
- .. (parent directory): Moves you one level up to the directory containing your current one.
- ~ (home directory): A shortcut to your personal home directory, like /home/pete.
- \- (previous directory): Takes you back to the last directory you were in.
