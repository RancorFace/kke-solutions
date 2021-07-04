# Linux String Substitute (sed)

## Task Details

There is some data on Nautilus App Server 1 in Stratos DC. Data needs to be altered in several of the files. On Nautilus App Server 1, alter the `/home/BSD.txt` file as per details given below:

a. Delete all lines containing word `code` and save results in `/home/BSD_DELETE.txt` file. (Please be aware of case sensitivity)

b. Replace all occurrence of word `the` to `them` and save results in `/home/BSD_REPLACE.txt` file.

Note: Let's say you are asked to replace word `to` with `from`. In that case, make sure not to alter any words containing this string; for example `upto`, `contributor` etc.

## Solution

* Login to backup server and switch to `root` user:

      ssh tony@stapp01
      sudo su -

* Count number of `code` strings in `/home/BSD.txt` file:

      grep code /home/BSD.txt | wc -l

* Delete lines with `code` string:

      sed '/code/d' BSD.txt > BSD_DELETE.txt

* Count number of `the` words in `/home/BSD.txt` file:

      grep -w or /home/BSD.txt | wc -l

* Substitute `the` with `them` words:

      sed 's/\bthe\b/them/g' BSD.txt > BSD_REPLACE.txt

## Verification

Verify files have been updated correctly using `diff` command, e.g. `diff /home/BSD.txt /home/BSD_DELETE.txt`.

---
For tips on getting better at KodeKloud Engineer Linux Administration tasks, [click here](./README.md)
