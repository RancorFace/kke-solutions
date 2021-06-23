# Create a Linux User with non-interactive shell

## Task Details

The System admin team of xFusionCorp Industries has installed a backup agent tool on all app servers. As per the tool's requirements they need to create a user with a non-interactive shell.

Therefore, create a user named `ravi` with a non-interactive shell in the App02 server.

## Solution

* Login to App02 server and switch to `root` user:

      ssh steve@stapp02
      sudo su -

* Verify user `ravi` does not exist:

      id ravi

* Create user `ravi` with non-interactive shell:

      useradd -s /sbin/nologin ravi

  __Note:__ You can use /sbin/nologin or /sbin/false. Verify files exist in your system or check other accounts in `/etc/passwd`.

## Verification

Validate user is created correctly:

      id ravi
      cat /etc/password | grep ravi
      su - ravi

---
For tips on getting better at KodeKloud Engineer Linux Administration tasks, [click here](./README.md)
