# Disable Root Login

## Task Details

After doing some security audits of servers, xFusionCorp Industries security team has implemented some new security policies. One of them is to disable direct root login through SSH.

Disable direct SSH root login on all app servers in Stratos Datacenter.

## Solution

* Login to each App Server and switch to `root`:

      ssh tony@stapp01
      sudo su -

* Disable direct SSH root login

      $ vi /etc/ssh/sshd_config
      PermitRootLogin no

* Reload SSH daemon configuration

      systemctl reload sshd.service

  **Optional:** Restart SSH service: `systemctl restart sshd && systemctl status sshd`

## Verification

Check status of root login setting using `grep PermitRootLogin /etc/ssh/sshd_config` on each app server.

---
For tips on getting better at KodeKloud Engineer Linux Administration tasks, [click here](./README.md)
