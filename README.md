megaclisas-status
=================

This will perform health checks on a MegaRAID device using the proper binary for your platform.

Debian information on the binaries are here: http://hwraid.le-vert.net/wiki/DebianPackages
Vendor provided binaries can be found here: http://www.lsi.com/Search/Pages/downloads.aspx?k=MegaCLI%20-%20Linux

Usage
=================
megaclisas-status [--nagios | --snmp | -q]

* no parameters: show megaraid info
* --nagios: show nagios-friendly output
* --snmp: show snmp MIB friendly output
* -q: Quiet mode, only displays output if an array or disk is bad - intended for use from cron.

Nagios Usage
=================
You can find a plugin, with instructions, here: http://exchange.nagios.org/directory/Plugins/System-Metrics/Storage-Subsystem/Raid-Check-using-megaclisas/details

SNMP Usage
=================
1. Install the MegaCLI Package for your platform
2. Copy this script to /usr/local/sbin and make it executable
3. Add the following to snmp.conf: extend megaraid /usr/local/sbin/megaclisas-status --snmp
4. Restart snmpd

The output MIB will be .1.3.6.1.4.1.8072.1.3.2.4.1.2.8.109.101.103.97.114.97.105.100

and the outputs are:
* .1 megaraid = 0, no megaraid = 1
* .2 Healthy = 0, Unhealthy = 1
* .3 number of good arrays
* .4 number of bad arrays
* .5 number of good disks
* .6 number of bad disks
