# Backup-Script

A collection of Bash scripts designed for robust, recursive, and incremental backups. This project provides multiple variants for different backup needs, including detailed reporting and integrity verification.

## Features

- **Incremental Backups**: Only files with newer timestamps in the source are updated in the backup.
- **Recursion**: Full directory tree traversal (configurable in specific scripts).
- **Exclusion Support**: Exclude specific directories or files using an external list (`-b` option).
- **Regex Filtering**: Filter files for backup using regular expressions (`-r` option).
- **Checking Mode**: Use the `-c` flag to simulate the backup process and see what would be changed without modifying any files.
- **Mirroring**: Automatically deletes files at the destination that have been removed from the source.
- **Safety Checks**:
  - Verifies read/write permissions for source and destination.
  - Checks for sufficient disk space before starting.
  - Detects and prevents recursive backup loops (source being a parent of destination).
- **Integrity Verification**: Compare source and backup using MD5 hashes to ensure data consistency.

## Project Structure

- `backup.sh`: The core backup script with recursion and full feature support.
- `backup_summary.sh`: An enhanced version of the core script that provides a detailed summary of operations (errors, warnings, copies, updates, deletions).
- `backup_check.sh`: A verification tool that uses MD5 hashes to compare source and destination contents.
- `backup_files.sh`: A simplified script for non-recursive, file-only backups.
- `utils.sh`: Shared utility functions used across all scripts.

## Usage

### Basic Backup
```bash
./backup.sh [OPTIONS] <source_directory> <destination_directory>
```

### Options
- `-c`: **Checking Mode**. Simulates the backup process.
- `-b <file>`: **Exclude Directories**. Provide a file containing paths to exclude.
- `-r <regex>`: **Regex Filter**. Only backup files matching the regex.

### Verification
To verify the integrity of a backup:
```bash
./backup_check.sh <source_directory> <destination_directory>
```

### Summary Report
To get a detailed report of the backup process:
```bash
./backup_summary.sh [OPTIONS] <source_directory> <destination_directory>
```

## License

This project is licensed under the [MIT License](LICENSE).

## Authors

Copyright (c) 2024 Eduardo Rosário & José Bagagem
