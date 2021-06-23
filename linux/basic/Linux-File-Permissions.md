# Linux File Permissions

## Task Details

There are new requirements to automate a backup process that was performed manually by the xFusionCorp Industries system admins team earlier. To automate this task, the team has developed a new bash script `xfusioncorp.sh`. They have already copied the script on all required servers, however they did not make it executable on one the app server i.e App Server 1 in Stratos Datacenter.

Please give executable permissions to `/tmp/xfusioncorp.sh` script on App Server 1. Also make sure every user can execute it.

### Explanation

**Question asks you to make sure every user is able to execute the script, not only the super user or sudo users.**

Since its a bash script not a normal file so it is asked to give it executable permission so that server users can run the script later whenever needed.

Please note that in case of bash script `bash` is the interpreter that is actually going to execute the script and the interpreter needs to read the script. Even if you have given it only executable permission the interpreter i.e `bash` will not be able to execute it. You have to give it read permission as well along with execute permission.

## Solution

* Login to stapp01 and change to `root`:

      ssh tony@stapp01
      sudo su -

* Add appropriate permissions to file:

      ls -l /tmp/xfusioncorp.sh
      chmod ugo+rx /tmp/xfusioncorp.sh

## Verification

Verify file permissions executing `ls -l /tmp/xfusioncorp.sh`.

---
For tips on getting better at KodeKloud Engineer Linux Administration tasks, [click here](./README.md)
