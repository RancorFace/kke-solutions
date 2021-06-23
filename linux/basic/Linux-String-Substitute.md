# Linux String Substitute

## Task Details

The backup server in the Stratos DC contains several template XML files used by the Nautilus application. However, these template XML files must be populated with valid data before they can be used. One of the daily tasks of a system admin working in the xFusionCorp industries is to apply string and file manipulation commands!

Replace all occurances of the string `Text` to `Sonar` on the XML file `/root/nautilus.xml` located in the backup server.

## Solution

* Login to backup server and switch to `root` user:

      ssh clint@stbkp01
      sudo su -

* Count number of `Text` strings in `/root/nautilus.xml` file:

      grep Text /root/nautilus.xml | wc -l

* Substitute `Text` with `Sonar` string:

      sed -i 's/Text/Sonar/g' /root/nautilus.xml

## Verification

Verify number of `Sonar` strings in `/root/nautilus.xml` file using `grep Sonar /root/nautilus.xml | wc -l`.

---
For tips on getting better at KodeKloud Engineer Linux Administration tasks, [click here](./README.md)
