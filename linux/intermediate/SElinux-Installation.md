# SElinux Installation

## Introduction

[What is SELinux?](https://www.redhat.com/en/topics/linux/what-is-selinux)  
[A Beginner's Guide to SELinux on CentOS 7](https://www.linode.com/docs/guides/a-beginners-guide-to-selinux-on-centos-7/)  
[CentOS SELinux HowTo](https://wiki.centos.org/HowTos/SELinux)  
[SELinux and Kubernetes](https://platform9.com/blog/selinux-kubernetes-rbac-and-shipping-security-policies-for-on-prem-applications/)

## Task Details

The xFusionCorp Industries security team recently did a security audit of their infrastructure and came up with ideas to improve the application and server security. They decided to use SElinux for an additional security layer. They are still planning how they will implement it; however, they have decided to start testing with app servers, so based on the recommendations they have the following requirements:

Install the required packages of SElinux on App server 3 in Stratos Datacenter and disable it permanently for now; it will be enabled after making some required configuration changes on this host. Don't worry about rebooting the server as there is already a reboot scheduled for tonight's maintenance window. Also ignore the status of SElinux command line right now; the final status after reboot should be `disabled`.

## Solution

* Login to App Server 3 and switch to `root`:

      ssh banner@stapp03
      sudo su -

* Install SELinux packages:

      yum install selinux -y
      yum install policycoreutils policycoreutils-python \
        selinux-policy selinux-policy-targeted \
        setools setools-console setroubleshoot -y

* Edit `/etc/selinux/config` file and set `SELINUX` variable to:

      SELINUX=disabled

## Verification

Validate the current status of SELinux running `sestatus` and verify SELinux state after reboot will be `disabled` by `grep "^SELINUX=" /etc/selinux/config`.

---
For tips on getting better at KodeKloud Engineer Linux Administration tasks, [click here](./README.md)
