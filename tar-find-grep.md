# Find 
find - search for files in a directory hierarchy

The following is theformat:

```
find [-H] [-L] [-P] [-D debugopts] [-Olevel] [starting-point...] [expression]
```
## Examples
find / -user jithu  -Find all files owned by user jithu
find / -size +5M /etc/	-Find all files more than 5MB in /etc directory
find / -user jithu -exec cp -rf {} /root/findresult/ \;	 -Find all files owned by user jithu and copy all the files to /root/findresult/ directory
find . -name thisfile.txt -Find file named thisfile.txt from present working directory

## More
find -O3 -L /var/www/ -name "*.html"
find /home -name *.jpg
find . -type f -empty
find /home -user randomperson-mtime 6 -iname ".db"
find / -name "*jpg" -mtime 5
find /home/randomuser/ -name "*jpg" -mtime 4
find . -type f -exec grep "forinstance" '{}' \; -print
find . -type f -print | xargs grep "forinstance"
find . -name "rc.conf" -exec chmod o+r '{}' \;
---
# grep 

grep, egrep, fgrep, rgrep - print lines that match patterns

```
grep [OPTION...] PATTERNS [FILE...]
grep [OPTION...] -e PATTERNS ... [FILE...]
grep [OPTION...] -f PATTERN_FILE ... [FILE...]
```

## Examples
`grep ^squid /usr/share/dict/words`  -Searching words starting with squid
`grep cat$ /usr/share/dict/words`  -Searching words ending with cat
`grep squid /usr/share/dict/words  > /etc/list.txt`  -Find the word squid from /usr/share/dict/words and redirect it to /etc/words file
---
# Tar
tar is an archiving utility,
Types of  Archiving and the extentions

|NO | Type | command |
|---|---|---|
| 1 | gzip | tar cfz |
| 2 | bzip2 | tar cfj |
| 3 | xz | tar cfJ |

## Examples

`tar xfz /root/archives/fstab.gzip /etc/fstab`  -archiving /etc/fstab to /root/archives/ directory with gzip
`tar xfj /root/archives/fstab.bzip2 /etc/fstab` -archiving /etc/fstab to /root/archives/ directory with bzip
`tar xfJ /root/archives/fstab.xz /etc/fstab`    -archiving /etc/fstab to /root/archives/ directory with xz
