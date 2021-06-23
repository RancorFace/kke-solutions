# Linux Archives

## Task Details

On Nautilus storage server in Stratos DC there is a storage location `/data` which is used by different developers to keep their data (no confidential data). One of the developers `ravi` has raised a ticket and asked for a copy of his/her data present in `/data/ravi` directory on storage server. `/home` is an FTP location on storage server where developers can download their data. Below are the instructions shared by the system admin team to accomplish the task:

Make a `ravi.tar.gz` compressed archive of `/data/ravi` directory and move the archive to `/home` directory on Storage Server.

## Solution

* Login to storage server and switch to `root` user:

      ssh natasha@ststor01
      sudo su -

* Compress `/data/ravi` directory:

      tar -czf ravi.tar.gz /data/ravi

* Move `ravi.tar.gz` archive file to `/home` directory:

      mv ravi.tar.gz /home

## Verification

Verify if archive file has been moved to `/home` using `ls -l /home`.

---
For tips on getting better at KodeKloud Engineer Linux Administration tasks, [click here](./README.md)
