# Create a user

## Task Details

For security reasons the xFusionCorp Industries security team has decided to use custom Apache users for each web application hosted, rather than its default user. This will be theApache user, so it shouldn't use the default home directory. Create the user as per requirements given below:

a. Create a user named `jim` on the App server 1 in Stratos Datacenter.

b. Set UID to `1349` and its home directory to `/var/www/jim`.

## Solution

* Login to App01 server and switch to `root` user:

      ssh tony@stapp01
      sudo su -

* Verify user `jim` does not exist:

      id jim

* Create user `jim` with appropriate UID and home directory:

      useradd -u 1349 -m -d /var/www/jim jim

## Verification

Validate user is created correctly with `cat /etc/password | grep jim`.

---
For tips on getting better at KodeKloud Engineer Linux Administration tasks, [click here](./README.md)
