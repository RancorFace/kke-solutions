# Linux TimeZones Setting

## Task Details

During the daily standup, it was pointed out that the timezone across Nautilus Application Servers in Stratos Datacenter doesn't match with that of the local datacenter's timezone, which is `Pacific/Efate`.

Correct the mismatch.

## Solution

* Login to each App Server and switch to `root`:

      ssh tony@stapp01
      sudo su -

* Correct the timezone:

      timedatectl
      timedatectl set-timezone Pacific/Efate

## Verification

Verify timezone using `timedatectl status` command.

---
For tips on getting better at KodeKloud Engineer Linux Administration tasks, [click here](./README.md)
