# Apache Troubleshooting

## Task Details

xFusionCorp Industries utilizes monitoring tools to check the status of every service, application, etc. running on the systems. The monitoring system identified that Apache service is not running on some of the Nautilus Application Servers in Stratos Datacenter.

Identify the faulty Nautilus Application Servers and fix the issue. Also, make sure Apache service is up and running on all Nautilus Application Servers. Do not try to stop any kind of firewall that is already running.

Apache is running on `8088` port on all Nautilus Application Servers and its document root must be `/var/www/html` on all app servers.

Finally you can test from jump host using curl command to access Apache on all app servers and it should work fine. E.g. `curl http://172.16.238.10:8088/`

## Solution

* Login to all App servers and switch to `root`:

      ssh tony@stapp01
      sudo su -

* Check status of Apache `httpd` service and try to start it if not running:

      systemctl status httpd
      systemctl start httpd

* Use `systemctl status httpd -l` to check if httpd started correctly and identify line and file where syntax error occurs. Optionally use `journalctl -u httpd` to check recent logs.

* Correct syntax error in `/etc/httpd/conf/httpd.conf` on specified line according to error message:

  1. Error:

         httpd: Syntax error on line 31 of /etc/httpd/conf/httpd.conf: ServerRoot must be a valid directory

     Correct following line:

         ServerRoot "/etc/httpd"

  2. Error:

         Invalid command 'Listen 8088', perhaps misspelled or defined by a module not included in the server configuration

     Correct following line:

         Listen 8088

  3. Error:

         DocumentRoot '/var/www/html;' is not a directory, or is not readable

     Correct following line:

         DocumentRoot /var/www/html

  4. Error:

         AH00558: httpd: Could not reliably determine the server's fully qualified domain name, using stapp01.stratos.xfusioncorp.com. Set the 'ServerName' directive globally to suppress this message

     Correct following line:

         ServerName stapp01.stratos.xfusioncorp.com:8088

* After each configuration update, restart `httpd` service using `systemctl restart httpd` and check status if there are no more errors.

* Execute `curl localhost:8088` to verify it returns expected content. If following error is returned:

      curl: (7) Failed to connect to ::1: Cannot assign requested address

  correct following line in `/etc/httpd/conf/httpd.conf` file:

      Listen 8088

## Verification

You can verify Apache `httpd` configuration file syntax using `httpd -t`.

If the status of `httpd` service is __active__, verify response from Apache `httpd` service of all App servers using `curl http://172.16.238.10:8088/` from `jump_host` server.

---
For tips on getting better at KodeKloud Engineer Linux Administration tasks, [click here](./README.md)
