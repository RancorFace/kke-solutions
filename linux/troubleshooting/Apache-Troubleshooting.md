# Apache Troubleshooting

## Task Details

xFusionCorp Industries utilizes monitoring tools to check the status of every service, application, etc. running on the systems. The monitoring system identified that Apache service is not running on some of the Nautilus Application Servers in Stratos Datacenter.

1. Identify the faulty Nautilus Application Servers and fix the issue. Also, make sure Apache service is up and running on all Nautilus Application Servers. Do not try to stop any kind of firewall that is already running.

2. Apache is running on `8085` port on all Nautilus Application Servers and its document root must be `/var/www/html` on all app servers.

3. Finally you can test from jump host using curl command to access Apache on all app servers and it should work fine. E.g. `curl http://172.16.238.10:8085/`

## Solution

* Login to all App servers and switch to `root`:

      ssh tony@stapp01
      sudo su -

* Check status of Apache `httpd` service and try to start it:

      systemctl status httpd
      systemctl start httpd

### Syntax error

* Use `systemctl status httpd` to check line and file where syntax error occurs.
* Correct syntax error on specified line in appropriate file.
* Start Apache `httpd` service and verify status:

      systemctl start httpd
      systemctl status httpd

## Verification

You can verify Apache `httpd` configuration file syntax using `httpd -t`.

If the status of `httpd` service is __active__, verify response from Apache `httpd` service of all App servers using `curl http://172.16.238.10:8085/` from `jump_host` server.

---
For tips on getting better at KodeKloud Engineer Linux Administration tasks, [click here](./README.md)
