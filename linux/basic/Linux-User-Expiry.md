# Linux User Expiry

## Task Details

A developer Mark has been assigned Nautilus project temporarily as a backup resource. As a temporary resource for this project, we need a temporary user for Mark. It's a good idea to create a user with a set expiration date so that the user won't be able to access servers beyond that point.

Therefore, create a user named `mark` on the _App Server 1_. Set `expiry date` to `2021-04-15` in Stratos Datacenter. Make sure the user is created as per standard and is in lowercase.

## Solution

* Login to App01 server and switch to `root` user:

      ssh tony@stapp01
      sudo su -

* Verify user `mark` does not exist:

      id mark

* Create user `mark` with account expiry date:

      useradd -e 2021-04-15 mark

  or

      useradd mark
      chage -E 2021-04-15 mark

## Verification

Validate changes are implemented  successfully using `chage -l mark`.

---
For tips on getting better at KodeKloud Engineer Linux Administration tasks, [click here](./README.md)
