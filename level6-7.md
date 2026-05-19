# Bandit Level 6 → 7

## Challenge
Password stored somewhere on the entire server.
Not just home directory. Millions of files to check.
Needed to filter by user, group and size.

## New Commands
find / -user bandit7 -group bandit6 -size 33c 2>/dev/null

## Command Meaning
- cd /          = go to root of entire system
- find /        = search everywhere on server
- -user bandit7 = file owned by user bandit7
- -group bandit6= file owned by group bandit6
- -size 33c     = exactly 33 bytes
- 2>/dev/null   = hide permission error messages
- /dev/null     = Linux trash bin for errors

## Why 2>/dev/null?
Searching entire server gives thousands of
permission denied errors. This hides them
so only the result we need is shown.

## Steps
cd /
find / -user bandit7 -group bandit6 -size 33c 2>/dev/null
cat /var/lib/dpkg/info/bandit7.password

## Flag
morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
