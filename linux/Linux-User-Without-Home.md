# Linux User Without Home

## Task Details

The system admins team of xFusionCorp Industries has set up a new tool on all app servers, as they have a requirement to create a service user account that will be used by that tool. They are finished with all apps except for _App 3_ in Stratos Datacenter.

Create a user named `yousuf` in __App Server 3__ without a home directory.

## Solution

* SSH to _App 3_ server and change to root user:

      ssh banner@stapp03
      sudo su -

* Create user `yousuf`:

      useradd -M yousuf

## Verification

List `/home` directory and verify `/home/yousuf` is not created.

---
For tips on getting better at KodeKloud Engineer Linux Administration tasks, [click here](./README.md)
