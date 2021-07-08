# Linux NTP Setup

## Task Details

The system admin team of xFusionCorp Industries has noticed an issue with some servers in Stratos Datacenter where some of the servers are not in sync w.r.t time. Because of this, several application functionalities have been impacted. To fix this issue the team has started using common/standard NTP servers. They are finished with most of the servers except App Server 2. Therefore, perform the following tasks on this server:

Install and configure NTP server on App Server 2.

Add NTP server `3.south-america.pool.ntp.org` in NTP configuration on App Server 2.

Please do not try to start/restart/stop `ntp` service, as we already have a restart for this service scheduled for tonight and we don't want these changes to be applied right now.

## Solution

* Login to App02 server and switch to `root`:

      ssh steve@stapp02
      sudo su -

* Check if NTP service is installed and install it:

      rpm -q ntp
      yum install ntp -y

* Add NTP server to configuration file:

      vi /etc/ntp.conf

  Add following line in appropriate section of configuration file:

      server 3.south-america.pool.ntp.org

* Enable NTP service to start after reboot:

      systemctl enable ntpd

## Verification

Verify if service is installed using `systemctl status ntpd` or `ntpstat`. Also you can check configuration file with `grep 3.south-america.pool.ntp.org /etc/ntp.conf`.

---
For tips on getting better at KodeKloud Engineer Linux Administration tasks, [click here](./README.md)
