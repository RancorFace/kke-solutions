# Linux Firewalld Rules

## Task Details

The Nautilus system admins team recently deployed a web UI application for their backup utility running on the Nautilus backup server in Stratos Datacenter. The application is running on port 8082. They have firewalld installed on that server. The requirements that have come up include the following:

Open all incoming connection on 8082/tcp port. Zone should be public.

## Solution

* SSH to backup server and note down the Apache port and Nginx ports respectively
* Execute following commands and verify the successful completion:

```UNIX
firewall-cmd --zone=public --permanent --add-port=8082/tcp
firewall-cmd --reload
firewall-cmd --list-all --zone=public
 ```  

## Verification

* Execute curl command from Jump Host to the web UI application port on backup server. You should see a valid response. For example - `curl -I http://stbkp01:8082/`

---
For tips on getting better at KodeKloud Engineer Linux Administration tasks, [click here](./README.md)
