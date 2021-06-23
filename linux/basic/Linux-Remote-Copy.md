# Linux Remote Copy

## Task Details

One of the Nautilus developers has copied confidential data on the jump host in Stratos DC. That data must be copied to one of the app servers. Because developers do not have access to app servers, they asked the system admins team to accomplish the task for them.

Copy `/tmp/nautilus.txt.gpg` file from jump server to __App Server 1__ at location `/home/webapp`.

## Solution

* At first scp the file to `stapp01`:

      scp /tmp/nautilus.txt.gpg  tony@stapp01:/tmp

* Login to app server and switch to `root` user (because `/home/webapp` is owned by `root`):

      ssh tony@stapp01
      sudo su

* Move file from `/tmp` directory to correct location:

      mv /tmp/nautilus.txt.gpg /home/webdata

  __Optional:__ Change ownership of the file:

      chown root:root /home/webdata/nautilus.txt.gpg

## Verification

List `/home/webapp` directory on __App Server 1__ using `ls -l /home/webapp`.

---
For tips on getting better at KodeKloud Engineer Linux Administration tasks, [click here](./README.md)
