## Find, Sort and Colorize Files by Size in a Directory Tree

This script is a useful tool for system administrators and users who need to find, sort, and colorize files by size in a directory tree. The script is designed to work in a Unix/Linux environment.

### Code

```bash
find /backup -maxdepth 5 -type f -exec du -sh {} \; | sort -rh | awk '{ printf "\033[1;33m%s\033[0m\t\033[1;36m%s\033[0m\n", $1, $2 }'


### Explanation

The script performs the following steps:

1. `find /backup -maxdepth 5 -type f -exec du -sh {} \;`: This command traverses the directory tree under `/backup`, up to a maximum depth of 5 levels, finds files (not directories), and for each file, it executes the `du -sh` command to calculate and print the disk usage in human-readable format (e.g., K, M, G).

2. `| sort -rh`: The output from the `find` command is piped (`|`) to `sort -rh`, which sorts the results in reverse order (`-r`) by human-readable sizes.

3. `awk '{ printf "\033[1;33m%s\033[0m\t\033[1;36m%s\033[0m\n", $1, $2 }'`: Finally, `awk` is used to print the sorted output with color. The ANSI color codes `\033[1;33m` and `\033[1;36m` are used to set the colors. `$1` and `$2` represent the file size and file name.


The script outputs the list of files with their sizes in descending order. The sizes are colorized in yellow, and filenames are colorized in cyan for better visibility.
