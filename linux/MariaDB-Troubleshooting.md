# MariaDB Troubleshooting

## Task Details

There is a critical issue going on with the Nautilus application in Stratos DC. The production support team identified that the application is unable to connect to the database. After digging into the issue, the team found that mariadb service is down on the database server.

Look into the issue and fix the same.

## Solution

* SSH to database server and change to root user using `sudo su -`
* Execute following commands to check status and start MariaDB service:

```UNIX
systemctl status mariadb
systemctl start mariadb
systemctl status mariadb
 ```

* Check MariaDB logs in /var/log/mariadb/mariadb.log
* If no logs available check ownership of MariaDB directories:
  * /var/run/mariadb
  * /var/lib/mysql
* Both should be owned by mysql:mysql, so correct ownership if needed using below commands:

```UNIX
chown mysql:mysql /var/run/mariadb
chown mysql:mysql /var/lib/mysql
```

* Start MariaDB service and verify its status:

```UNIX
systemctl start mariadb
systemctl status mariadb
 ```

## Verification

<!--* Execute curl command from Jump Host to the web UI application port on backup server. You should see a valid response. For example - `curl -I http://stbkp01:8082/`-->

---
For tips on getting better at KodeKloud Engineer Linux Administration tasks, [click here](./README.md)
