# Linux User Files

## Task Details

There was some users data copied on Nautilus App Server 1 at `/home/usersdata` location by the Nautilus production support team in Stratos DC. Later they found that they mistakenly mixed up different user data there. Now they want to filter out some user data and copy it to another location. Find the details below:

On App Server 1 find all files (not directories) owned by user `mark` inside `/home/usersdata` directory and copy them all __while keeping the folder structure__ (preserve the directories path) to `/news` directory.

## Solution

* Login to App01 server and switch to `root`:

  ```UNIX
  ssh tony@stapp01
  sudo su -
  ```

* Copy all file owned by `mark` user under `/home/usersdata` to `/news`:

  ```UNIX
  find /home/usersdata/ -user ammar -exec cp --parents {} /ecommerce \;
  ```

## Verification

Verify if all files have been copied correctly executing these commands:

```UNIX
cd /home/usersdata/
find * -user mark > ~/mark.out
cd /news
find * -type f > ~/news.out
cd
diff mark.out news.out
```

`diff` command should return no result (no differences between files).

---
For tips on getting better at KodeKloud Engineer Linux Administration tasks, [click here](./README.md)
