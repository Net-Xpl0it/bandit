# Bandit Level 5 → 6

## Challenge
Password hidden inside one of 20 directories
with hundreds of files. Impossible to check manually.
Needed to filter by file properties.

## New Command
find . -size 1033c ! -executable

## Command Meaning
- find        = search for files
- .           = search in current directory
- -size       = filter by file size
- 1033c       = exactly 1033 bytes (c = bytes)
- !           = means NOT
- -executable = runnable program files

## Steps
cd inhere/
find . -size 1033c ! -executable
cat ./maybehere07/.file2 | head -1

## Flag
HWasnPhtq9AVKe0dmk45nxy20cvUaGEG
