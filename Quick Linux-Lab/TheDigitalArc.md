# The Digital Architect

## Setting Up the Project Directory Structure

Your first task is to create a proper directory structure inside the phoenix_project directory. A well-defined structure separates different types of files, making the project easier to navigate and maintain.

Tasks
Navigate into the ~/project/phoenix_project directory.
Create three new subdirectories: src for source code, config for configuration files, and docs for documentation.
Requirements
All new directories must be created inside the ~/project/phoenix_project directory.
The directory names must be exactly src, config, and docs.
You should use a single command to create all three directories simultaneously.
Examples
After completing this step, your directory structure should look like this:

~/project/phoenix_project/
├── config/
├── docs/
├── src/
├── README.md
├── config.json
└── main_app.py
 Explain Code
When you run ls -F in the ~/project/phoenix_project directory, you should see:

README.md  config/  config.json  docs/  main_app.py  src/
 Explain Code
The / symbols after directory names indicate they are directories, not files.

Hints
Use the cd command to change your current directory.
The mkdir command is used to create new directories.
mkdir can accept multiple arguments to create several directories at once.

---

## Navigating and Creating Project files

With the new directory structure in place, it's time to move the existing project files into their designated homes. This will clean up the root of the project and make files easier to find.

Tasks
Move the main_app.py file into the src directory.
Move the config.json file into the config directory.
Move the README.md file into the docs directory.
Requirements
Ensure you are in the ~/project/phoenix_project directory before performing the move operations.
Use the mv command to relocate each file.
Examples
After moving the files, your project structure should be organized like this:

~/project/phoenix_project/
├── config/
│ └── config.json
├── docs/
│ └── README.md
└── src/
└── main_app.py
 Explain Code
When you run ls -F in the root ~/project/phoenix_project directory, it should show only the directories:

config/  docs/  src/
 Explain Code
Each file should now be in its appropriate subdirectory:

ls src/ → main_app.py
ls config/ → config.json
ls docs/ → README.md
Hints
The mv command is used to move or rename files and directories.
The basic syntax is mv [SOURCE] [DESTINATION].
For example, to move file.txt into a directory named documents, you would use mv file.txt documents/.

---

## Backing Up Critical Configuration files

The config.json file contains critical settings for Project Phoenix. Before any modifications are made, it's a vital safety measure to create a backup. Your next task is to create a copy of this file.

Tasks
Create a backup copy of the config.json file.
Requirements
The backup file must be created within the ~/project/phoenix_project/config/ directory.
The backup file must be named exactly config.json.bak.
Examples
After creating the backup, your config directory should contain both files:

~/project/phoenix_project/config/
├── config.json
└── config.json.bak
 Explain Code
When you run ls in the ~/project/phoenix_project/config/ directory, you should see:

config.json  config.json.bak
 Explain Code
Both files should have identical content, as the .bak file is an exact copy of the original:

 These commands should show identical output
cat config.json
cat config.json.bak
 Explain Code
Hints
The cp command is used to copy files and directories.
The syntax is cp [SOURCE] [DESTINATION].
You will need to provide the full path to the source file and the full path for the new backup file.

---

## Reorganizing the Team’s Shared Resources
You've discovered another piece of the puzzle: a directory named shared_docs located at ~/project/shared_docs. This directory contains important team guidelines and API specifications that belong with the rest of the project's documentation. Your task is to integrate it into the main project structure.

Tasks
Move the entire shared_docs directory and all of its contents into the ~/project/phoenix_project/docs/ directory.

Requirements
The source directory is ~/project/shared_docs.
The destination path is ~/project/phoenix_project/docs/.
The entire directory, not just its contents, must be moved.
Examples
After moving the shared_docs directory, your documentation structure should look like this:

~/project/phoenix_project/docs/
├── README.md
└── shared_docs/
├── api_spec.doc
└── team_guidelines.txt
 Explain Code
When you run ls in the ~/project/phoenix_project/docs/ directory, you should see:

README.md  shared_docs/
 Explain Code
The shared_docs directory should contain all its original files:

ls ~/project/phoenix_project/docs/shared_docs/
 Explain Code
api_spec.doc  team_guidelines.txt
 Explain Code
The original location ~/project/shared_docs should no longer exist.

Hints
The mv command works for directories just as it does for files.
When you move a directory, all of its contents are moved with it automatically.
The command will look like mv [SOURCE_DIRECTORY] [DESTINATION_DIRECTORY]

---

## Archiving and Removing Outdated Log files

Your final task is a bit of housekeeping. The ~/project/logs directory is accumulating log files, and the ones from 2023 are no longer needed for daily operations. To save space and keep things tidy, you need to compress these old logs into a single archive file and then remove the original files.

Understanding the tar Command
The tar command is a powerful Linux tool for creating and manipulating archive files. "Tar" originally stood for "Tape Archive" because it was designed to write data to magnetic tapes, but today it's commonly used to create compressed archive files on disk.

When you use tar, you're essentially bundling multiple files together into a single file (called an archive), and you can optionally compress this archive to save space. The most common compression format is gzip, which adds the .gz extension to the filename.

The tar command uses different options (flags) to control its behavior:

c: Create a new archive
z: Compress the archive using gzip
f: Specify the filename of the archive
So tar -czf archive.tar.gz file1 file2 creates a new compressed archive named archive.tar.gz containing file1 and file2.

Tasks
Navigate to the ~/project/logs directory.
Create a compressed tar archive named old_logs.tar.gz that contains all log files from the year 2023.
After the archive is successfully created, delete the original 2023 log files that you just archived.
Requirements
The final archive must be named exactly old_logs.tar.gz.
The archive must be located in the ~/project/logs directory.
Only log files with 2023 in their name should be archived and subsequently removed.
The log file from 2024 (app_2024-05-01.log) must not be included in the archive and must not be deleted.
Examples
Before archiving, your logs directory contains:

~/project/logs/
├── app_2023-01-15.log
├── app_2024-05-01.log
└── db_2023-02-20.log
 Explain Code
After completing the archiving task, your logs directory should look like:

~/project/logs/
├── app_2024-05-01.log
└── old_logs.tar.gz
 Explain Code
When you run ls in the ~/project/logs/ directory, you should see:

app_2024-05-01.log  old_logs.tar.gz
 Explain Code
Hints
Use the tar command to create archives. The options -czf are a powerful combination: c (create), z (compress with gzip), and f (specify filename).
You can use a wildcard (*) to select multiple files that match a pattern. For example, *_2023-*.log will match all files that end with .log and have _2023- in their name.
The rm command is used to remove (delete) files. Be careful when using it with wildcards!``




