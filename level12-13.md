# Bandit Level 12 → 13

## Challenge
data.txt was a hexdump of a repeatedly compressed file.
Needed to reverse the hexdump then decompress
multiple times through different compression formats
to finally get the password.

## Workspace Setup
mktemp -d
# creates random temp folder in /tmp
# used because bandit12 has no write permission in home

cp ~/data.txt /tmp/tmp.K2OKMhQndh
cd /tmp/tmp.K2OKMhQndh

## Step 1 - Reverse Hexdump
xxd -r data.txt > data
# xxd    = hex tool
# -r     = reverse mode (hexdump → binary)
# > data = save output as new file

## Step 2 - gzip
file data
# result: gzip compressed data
mv data data.gz
gzip -d data.gz
# gzip -d = decompress gzip file

## Step 3 - bzip2
file data
# result: bzip2 compressed data
mv data data.bz2
bzip2 -d data.bz2
# bzip2 -d = decompress bzip2 file

## Step 4 - gzip again
file data
# result: gzip compressed data
mv data data.gz
gzip -d data.gz

## Step 5 - tar
file data
# result: POSIX tar archive
mv data data.tar
tar xf data.tar
# tar xf = extract tar archive
# x = extract
# f = filename

## Step 6 - tar again
file data5.bin
# result: POSIX tar archive
tar xf data5.bin

## Step 7 - bzip2 again
file data6.bin
# result: bzip2 compressed data
mv data6.bin data6.bz2
bzip2 -d data6.bz2

## Step 8 - tar again
file data6
# result: POSIX tar archive
tar xf data6

## Step 9 - gzip again
file data8.bin
# result: gzip compressed data
mv data8.bin data8.gz
gzip -d data8.gz

## Final
file data8
# result: ASCII text
cat data8

## Compression Types Learned
| Command      | Format | Flag |
|--------------|--------|------|
| gzip -d      | .gz    | -d = decompress |
| bzip2 -d     | .bz2   | -d = decompress |
| tar xf       | .tar   | x = extract, f = file |
| xxd -r       | hex    | -r = reverse |

## Flag
FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn
