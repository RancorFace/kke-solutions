# Linux Services

## Task Details

As per details shared by the development team, the new application release has some dependencies on the back end. There are some packages/services that need to be installed on all app servers under Stratos Datacenter. As per requirements please perform the following steps:

a. Install `httpd` package on all the application servers.

b. Once installed, make sure it is enabled to start during boot.

## Solution

* Login to each App Server and switch to `root`:

      ssh tony@stapp01
      sudo su -

* Install `httpd` package:

      yum install httpd -y

* Start & enable the httpd service:

      systemctl start httpd
      systemctl enable httpd

## Verification

Check status of `httpd` service using `systemctl status httpd`.

---
For tips on getting better at KodeKloud Engineer Linux Administration tasks, [click here](./README.md)
