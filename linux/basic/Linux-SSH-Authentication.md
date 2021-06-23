# Linux SSH Authentication

## Task Details

The system admins team of xFusionCorp Industries has set up some scripts on jump host that run on regular intervals and perform operations on all app servers in Stratos Datacenter. To make these scripts work properly we need to make sure `thor` user on jump host has password-less SSH access to all app servers through their respective sudo users. Based on the requirements, perform the following:

Set up a password-less authentication from user `thor` on jump host to all app servers through their respective sudo users.

## Solution

* Generate SSH key pair on jump host:

      ssh-keygen -t rsa -b 4096

* Copy SSH public key to each app server:

      ssh-copy-id tony@stapp01
      ssh-copy-id steve@stapp02
      ssh-copy-id banner@stapp03

## Verification

Verify if password is required when log in to each app server, e.g. `ssh tony@stapp01`.

---
For tips on getting better at KodeKloud Engineer Linux Administration tasks, [click here](./README.md)
