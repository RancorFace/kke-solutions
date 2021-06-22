# Linux Collaborative Directories

## Introduction

### Special permission explained

Special permissions make up a fourth access level in addition to **user**, **group**, and **other**. Special permissions allow for additional privileges over the standard permission set.

### SUID: user + s (pecial)

The special permission for the user access level has a single function: A file with **SUID** always executes as the user who owns the file, regardless of the user passing the command. If the file owner doesn't have execute permissions, then use an uppercase **S** here.

To see this in a practical light, let's look at the `/usr/bin/passwd` command. This command, by default, has the SUID permission set:

```UNIX
$ ls -l /usr/bin/passwd 
-rwsr-xr-x. 1 root root 33544 Jun 22 11:31 /usr/bin/passwd
```

### SGID: group + s (pecial)

This special permission has a couple of functions:

* If set on a file, it allows the file to be executed as the **group** that owns the file (similar to SUID)
* If set on a directory, any files created in the directory will have their **group** ownership set to that of the directory owner

```UNIX
$ ls -l 
total 0
drwxrws---. 2 pkrol pkrol  69 Jun 22 11:31 sample_file
```

This permission set is noted by a lowercase **s** where the **x** would normally indicate **execute** privileges for the **group**. It is also especially useful for directories that are often used in collaborative efforts between members of a group. Any member of the group can access any new file. This applies to the execution of files, as well. If the owning group does not have execute permissions, then an uppercase **S** is used.

### other + t (sticky)

The last special permission has been dubbed the "sticky bit." This permission does not affect individual files. However, at the directory level, it restricts file deletion. Only the **owner** (and **root**) of a file can remove the file within that directory. A common example of this is the `/tmp` directory:

```UNIX
$ ls -ld /tmp/
drwxrwxrwt. 15 root root 4096 Sep 22 15:28 /tmp/
```

The permission set is noted by the lowercase **t**, where the **x** would normally indicate the execute privilege.

### Setting special permissions

To set special permissions on a file or directory, you can utilize either symbolic or numerical method.

Let's assume that we want to set **SGID** on the directory `community_content`.

To do this using the symbolic method, we do the following:

```UNIX
chmod g+s community_content/
```

Using the numerical method, we need to pass a fourth, preceding digit in our `chmod` command. The digit used is calculated similarly to the standard permission digits:

```UNIX
Start at 0
SUID = 4
SGID = 2
Sticky = 1
```

The syntax is:

```UNIX
chmod X### <file | directory>
```

Where **X** is the special permissions digit.

Here is the command to set **SGID** on `community_content` using the numerical method:

```UNIX
$ chmod 2770 community_content/
$ ls -ld community_content/
drwxrws---. 2 pkrol pkrol 113 Apr  7 11:32 community_content/
```

## Task Details

The Nautilus team doesn't want its data to be accessed by any of the other groups/teams due to security reasons and want their data to be strictly accessed by the `devops` group of the team.

Setup a collaborative directory `/devops/data` on Nautilus App 3 server in Stratos Datacenter.

The directory should be group owned by the group `devops` and the group should own the files inside the directory. The directory should be `read/write/execute` to the group owners, and `others` should not have any access.

## Solution

* Login to App01 server and switch to `root` user:

  ```UNIX
  ssh tony@stapp01
  sudo su -
  ```

* Create `/devops/data/` directory:

  ```UNIX
  mkdir -p /devops/data
  ```

* Change group ownership of `/devops` directory and all subdirectories:

  ```UNIX
  chgrp -R devops /devops
  ```

* Change permissions of `/devops` directory:

  ```UNIX
  chmod -R 2770 /devops
  ```

## Verification

Verify `/devops` directory has appropriate permissions using `ls -l /devops`:

```UNIX
$ ls -l /devops
total 0
drwxrws--- 1 root devops 4096 Jun 22 18:41 data
```

---
For tips on getting better at KodeKloud Engineer Linux Administration tasks, [click here](./README.md)
