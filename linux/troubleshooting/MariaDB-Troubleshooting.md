# MariaDB Troubleshooting

## Task Details

There is a critical issue going on with the Nautilus application in Stratos DC. The production support team identified that the application is unable to connect to the database. After digging into the issue, the team found that `mariadb` service is down on the database server.

Look into the issue and fix the same.

## Solution

* SSH to database server and change to `root`:

      ssh peter@stdb01
      sudo su -

* Check status of MariaDB service and try to start it:

      systemctl status mariadb
      systemctl start mariadb
      systemctl status mariadb

* Check MariaDB logs in `/var/log/mariadb/mariadb.log` for error message.

### No logs in /var/log/mariadb/mariadb.log

* Verify ownership of MariaDB directories:
  * /var/run/mariadb
  * /var/lib/mysql  

  Both should be owned by mysql:mysql, so correct ownership if needed:

      chown mysql:mysql /var/run/mariadb
      chown mysql:mysql /var/lib/mysql

* Start MariaDB service and verify its status:

      systemctl start mariadb

## Verification

Verify mariadb service is running using `systemctl status mariadb`.

---
For tips on getting better at KodeKloud Engineer Linux Administration tasks, [click here](./README.md)
