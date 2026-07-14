# User Account Management

How to create, modify, and delete user accounts, as well as how to set and change passwords. These are fundamental skills for Linux system administration.

> **Note:** Most commands here require administrator privileges, so they are prefixed with `sudo`. Running them as a regular user results in a "permission denied" error.

## Creating a New User

Let's start by creating a new user account named `joker`.

```bash
sudo useradd joker
```

Breaking this down:

- `sudo` gives you temporary superuser (administrator) privileges. Creating a new user requires these higher-level permissions.
- `useradd` is the command to create a new user.
- `joker` is the username we're creating.

To verify that the user was created, examine the `/etc/passwd` file:

```bash
sudo grep -w 'joker' /etc/passwd
```

The `/etc/passwd` file is like a phonebook for user accounts. Each line represents one account, with fields separated by colons (`:`). You should see output similar to:

```plaintext
joker:x:5001:5001::/home/joker:/bin/sh
```

This line shows:

| Field | Value | Meaning |
| --- | --- | --- |
| Username | `joker` | The account name. |
| Password | `x` | The actual password is stored securely elsewhere. |
| User ID | `5001` | Numeric user ID (UID). |
| Group ID | `5001` | Numeric group ID (GID). |
| Home Directory | `/home/joker` | Not created yet in this case. |
| Default Shell | `/bin/sh` | The login shell. |

## Creating a User with a Home Directory

Now let's create another user named `bob` and give them a home directory.

```bash
sudo useradd -m bob
```

The `-m` option tells the system to create a home directory for the user — a personal folder where they can store files and settings.

Verify that the home directory was created:

```bash
sudo ls -ld /home/bob
drwxr-x--- 2 bob bob 57 Jan 19 13:33 /home/bob
```

This output shows:

- `d` at the start means it's a directory.
- `rwxr-x---` shows who can read, write, or execute in this directory.
- The two `bob` entries show that both the user and group owner of this directory is `bob`.
- `57` is the size of the directory in bytes.
- `Jan 19 13:33` is when the directory was created.
- `/home/bob` is the location of the directory.

## Setting a User Password

Now we need to set a password for our new users. Let's set one for `joker`.

```bash
sudo passwd joker
```

You'll be asked to enter a new password twice. For this lab, use a simple password like `password123`.

- **The password will not be displayed as you type it.** This is a security feature that prevents others from seeing your password.
- If successful, you'll see `passwd: password updated successfully`.
- In a real-world scenario, always use strong, unique passwords.

Behind the scenes, Linux stores encrypted passwords in a secure file called `/etc/shadow`. This is more secure than storing them in `/etc/passwd`, where anyone could read them.

## Modifying User Properties

Linux lets us change various settings for a user account after it's been created. Let's change joker's home directory as an example.

```bash
sudo usermod -d /home/wayne joker
```

Here's what this does:

- `usermod` is the command to modify user account settings.
- `-d /home/wayne` specifies the new home directory.
- `joker` is the user we're modifying.

Verify the change:

```bash
sudo grep -w 'joker' /etc/passwd
```

`-w` matches the whole word, and `grep` searches for it in the file. You should see that joker's home directory has been updated.

## Changing a User's Shell

Another important setting is the user's default shell — the program that interprets and runs the commands you type in the terminal.

By default, `joker` uses `/bin/sh`. While `sh` (Bourne Shell) is a basic shell present on most Unix-like systems, `bash` (Bourne Again Shell) offers more features and is generally more user-friendly.

Change joker's default shell to bash:

```bash
sudo usermod -s /bin/bash joker
```

Verify the change:

```bash
sudo grep -w 'joker' /etc/passwd
```

You should see `/bin/bash` at the end of joker's entry. This means bash is now joker's default shell.

## Adding a User to a Group

In Linux, we use groups to organize users and manage permissions. One important group is the `sudo` group, which grants users administrative privileges. Let's add joker to it.

**Why add a user to the `sudo` group instead of just using the `sudo` command?**

- **Convenience:** Members can use `sudo` with their own password, without needing the root password.
- **Granular control:** Administrators can configure `sudo` to allow specific users to run only certain commands.
- **Accountability:** Unlike sharing the root password, `sudo` logs who ran what command, improving security and traceability.
- **Security:** Named accounts with `sudo` access are safer than sharing one root password among many admins.

Now, add joker to the sudo group:

```bash
sudo usermod -aG sudo joker
```

Here's what this does:

- `usermod` modifies user accounts.
- `-aG` means "append to Group" — add to a group without removing the user from other groups.
- `sudo` is the group we're adding the user to.
- `joker` is the user we're modifying.

Verify the change:

```bash
groups joker
```

You should see `sudo` listed among joker's groups.

To test it, switch to the joker user and try a command that requires root privileges:

```bash
su - joker
```

This switches from your current user to `joker`. You'll be prompted for joker's password (`password123`). Once logged in as joker, try to view a file that normally requires root privileges:

```bash
sudo cat /etc/shadow
```

Enter joker's password again when prompted. You should be able to see the contents of `/etc/shadow`, which confirms that joker now has `sudo` privileges. Type `exit` to return to your original account.

> **In production, be very careful about who you add to the `sudo` group.** With great power comes great responsibility.

## Locking and Unlocking User Accounts

Sometimes you need to temporarily disable a user account without deleting it.

Lock the joker account:

```bash
sudo passwd -l joker
```

The `-l` option locks the password. Now try to switch to the joker user:

```bash
su - joker
```

Enter joker's password. You should see an "authentication failure" message, which means the account is successfully locked.

Now unlock the account:

```bash
sudo passwd -u joker
```

The `-u` option unlocks the password. Try switching again — this time it should succeed. Type `exit` to return to your original account.

## Deleting a User

Finally, let's delete the `bob` user we created earlier, along with their home directory.

```bash
sudo userdel -r bob
```

The `userdel` command deletes user accounts. The `-r` option removes the user's home directory and mail spool.

Verify that the user has been deleted:

```bash
sudo grep -w 'bob' /etc/passwd
sudo ls -ld /home/bob
```

Both commands should return no results, confirming the user and their home directory were removed.

## Summary

You've learned how to:

- Create new user accounts (`useradd`, `useradd -m`).
- Set user passwords (`passwd`).
- Modify user properties like home directory and default shell (`usermod -d`, `usermod -s`).
- Add users to groups (`usermod -aG`).
- Lock and unlock user accounts (`passwd -l`, `passwd -u`).
- Delete user accounts (`userdel -r`).

You were also introduced to important Linux concepts like the `/etc/passwd` file, home directories, shells, and user groups. In real-world scenarios, always follow your organization's security policies when managing user accounts.
