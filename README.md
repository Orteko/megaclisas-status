megaclisas-status
=================

Original docs : http://hwraid.le-vert.net/wiki/DebianPackages

Usage
=================
megaraid-status [--nagios|--snmp]

* no parameters : show megaraid info
* --nagios : show nagios-friendly output
* --snmp : show snmp MIB friendly output

Nagios Usage
=================
TBD

SNMP Usage
=================
1. Install the MegaCLI Package
2. Copy this script to /usr/local/sbin and make it executable
3. Add the following to snmp.conf : 
    extend megaraid /usr/local/sbin/megaclisas-status --snmp 
4. restart snmpd

The output MIB will be .1.3.6.1.4.1.8072.1.3.2.4.1.2.8.109.101.103.97.114.97.105.100

and the outputs are :
.1 megaraid = 0, no megaraid = 1
.2 Healthy = 0, Unhealthy = 1
.3 number of good arrays
.4 number of bad arrays
.5 number of good disks
.6 number of bad disks

