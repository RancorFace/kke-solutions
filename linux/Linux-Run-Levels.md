# Linux Run Levels

## Task Details

New tools have been installed on the app server in Stratos Datacenter. Some of these tools can only be managed from the graphical user interface. Therefore, there are requirements for these app servers.

On all App servers in Stratos Datacenter change the default runlevel so that they can boot in GUI (graphical user interface) by default.

## Solution

* Login to each App Server and switch to `root`:

      ssh tony@stapp01
      sudo su -

* Change default runlevel to graphical user interface:

      systemctl set-default graphical.target

## Verification

Verify default runlevel using `systemctl get-default` command.

---
For tips on getting better at KodeKloud Engineer Linux Administration tasks, [click here](./README.md)
