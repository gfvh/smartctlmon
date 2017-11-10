# smartctl smartmontools snmp monitoring solution 

## Whats new:

#### Forked from mad-hacking website
#### Adjusted scripts and snmp mibs files

## Structure:

### smartctlmon

-> snmp/
-> etc  lib  mibs  sbin  var

## Files:

snmp/etc/
snmpd-smartctl-connector
snmpd.conf < extend pass with OID to script callout

snmp/lib/    
hk-bash.sh < bourne shell functions script
snmpd-connector-lib.sh < connector

snmp/sbin/
snmpd-smartctl-connector
update-smartctl-cache

snmp/mibs/
SMARTCTL-MIB.txt < MIB definations
SMARTCTL-PLUS-MIB.txt < MIB def.

zabbix_templates/
Template_Supermicro_Superdoctor5_SNMP_LLDv2.xml < custom zabbix template what has also superdoctor5 other functions

Template_Smartmontools_SNMP.xml < single file for disk status only

Supermicro_OS_standard_plus_HW.xml < main template file what links

Bundled together: smartctlmon.tar

### Installing:

#### Depending on OS smartmontools is needed as well.

1. Copy dir/files to /opt/smartctlmon/
2. Enable SNMPD conf. Look at file example
3. Run first time script update-smartctl-cache and add it to crontab 10 minutes interval
4. For zabbix import Template_Supermicro_Superdoctor5_SNMP_LLDv2.xml

### To get superdoctor5 mon functions you need to install it separately

## Tests:

snmptranslate -Tp SMARTCTL-MIB::smartCtlTable
snmpwalk -c "replacewithcommunityname" -v2c localhost SMARTCTL-MIB::smartCtlTable
