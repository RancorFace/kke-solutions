# Linux Postfix Troubleshooting

## Task Details

Some users of the monitoring app have reported issues with xFusionCorp Industries mail server. They have a mail server in Stork DC where they are using `postfix` mail transfer agent. `Postfix` service seems to fail. Try to identify the root cause and fix it.

## Solution

* Login to mail server and switch to `root` user:

      ssh groot@stmail01
      sudo su -

* Check statos of `postfix` service and system logs:

      systemctl status postfix -l
      journalctl -u postfix.service

* Correct duplicated `inet_interface` parameter:

      vi /etc/postfix/main.cf

      inet_interfaces = all
      #inet_interfaces = localhost

* Start `postfix` service:

      systemctl start postfix

## Verification

Verify the service is running using `systemctl status postfix`.

---
For tips on getting better at KodeKloud Engineer Linux Administration tasks, [click here](./README.md)
