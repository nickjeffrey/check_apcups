# check_apcups
nagios / zenoss check for APC UPS with SNMP management card with temperature / humidity sensors

Refer to embedded documentation in script for usage details

# Requirements
perl, snmpget on nagios server

# Configuration

 You will need a section in the services.cfg file on the nagios server that looks similar to the following.
```
      # Define a service to check the APC UPS
      # Parameters are SNMP community name
      define service {
              use                             generic-service
              hostgroup_name                  all_apcups
              service_description             APC UPS
              check_command                   check_apcups!public
              }
```

You will also need a command definition similar to the following in commands.cfg on the nagios server
```
      # 'check_apcups' command definition
      # parameters are -H hostname -C snmp_community
      define command{
              command_name    check_apcups
              command_line    $USER1$/check_apcups -H $HOSTADDRESS$ -C $ARG1$
              }
```
