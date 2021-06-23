# DNS Troubleshooting

## Task Details

The system admins team of xFusionCorp Industries has noticed intermittent issues with DNS resolution in several apps . App Server 1 in Stratos Datacenter is having some DNS resolution issues, so we want to add some additional DNS nameservers on this server.

As a temporary fix we have decided to go with Google public DNS (ipv4). Please make appropriate changes on this server.

## Solution

* Login to App server 1 and switch to `root` user:

      ssh tony@stapp01
      sudo su -

* Update local DNS configuration

      vi /etc/resolv.conf

  and change from:

      nameserver 127.0.0.11

  to:

      nameserver 8.8.4.4
      nameserver 8.8.8.8

## Verification

Print contents of `/etc/resolv.conf` and compare to this output:

      search stratos.xfusioncorp.com
      #nameserver 127.0.0.11
      nameserver 8.8.4.4
      nameserver 8.8.8.8
      options ndots:0

---
For tips on getting better at KodeKloud Engineer Linux Administration tasks, [click here](./README.md)
