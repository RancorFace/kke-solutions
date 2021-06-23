# Create a Cron Job

## Task Details

The Nautilus system admins team has prepared scripts to automate several day-to-day tasks. They want them to be deployed on all app servers in Stratos DC on a set schedule. Before that they need to test similar functionality with a sample cron job. Therefore, perform the steps below:

a. Install `cronie` package on all Nautilus app servers and start `crond` service.

b. Add a cron `*/5 * * * * echo hello > /tmp/cron_text` for `root` user.

## Solution

* Login to all App servers and switch to `root`:

      ssh tony@stapp01
      sudo su -

* Install `cronie` package:

      yum install cronie

* Start `crond` service and check its status:

      systemctl start crond
      systemctl status crond

* Edit crontab:

      crontab -e

  Enter cron job and save the crontab:

      */5 * * * * echo hello > /tmp/cron_text

## Verification

Verify `crond` service is running using `systemctl status crond` and check crontab entry with `crontab -l`.

---
For tips on getting better at KodeKloud Engineer Linux Administration tasks, [click here](./README.md)
