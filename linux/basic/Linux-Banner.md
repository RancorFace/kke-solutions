# Linux Banner

## Task Details

During the monthly compliance meeting, it was pointed out that several servers in the Stratos DC do not have a valid banner. The security team has provided several approved templates which should be applied to the servers to maintain compliance. These will be displayed to the user upon a successful login.

Update the `message of the day` on all application and db servers for Nautilus. Make use of the approved template located at `/tmp/nautilus_banner` on jump host.

## Solution

* At first scp `/tmp/nautilus_banner` file to all App & DB servers:

      scp /tmp/nautilus_banner  tony@stapp01:/tmp

* Login to App & DB servers and switch to `root` user:

      ssh tony@stapp01
      sudo su -

* Move file from `/tmp` directory to correct location:

      mv /tmp/nautilus_banner /etc/motd

## Verification

Login to all servers and check banner has been implemented successfully.

---
For tips on getting better at KodeKloud Engineer Linux Administration tasks, [click here](./README.md)
