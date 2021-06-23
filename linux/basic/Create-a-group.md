# Create a group

## Task Details

There are specific access levels for users defined by the xFusionCorp Industries system admin team. Rather than providing access levels to every individual user, the team has decided to create groups with required access levels and add users to that groups as needed. See the following requirements:

a. Create a group named `nautilus_developers` in all App servers in Stratos Datacenter.

b. Add the user `mohammed` to `nautilus_developers` in all App servers. (create the user if not present already)

## Solution

* Login to all App servers and switch to `root`:

      ssh tony@stapp01
      sudo su -

* Create group:

      groupadd nautilus_developers

* Check user is already present:

      id mohammed

* Create new user if required:

      useradd -G nautilus_developers mohammed

  Or add existing user to the group:

      usermod -a -G nautilus_developers mohammed

## Verification

Verify user `mohammed` is member of `nautilus_developers` group using `groups mohammed` or `id -nG mohammed`.

---
For tips on getting better at KodeKloud Engineer Linux Administration tasks, [click here](./README.md)
