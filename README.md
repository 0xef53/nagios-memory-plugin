Nagios memory plugin
--------------------

It's a plugin for checking memory usage for Nagios compatible monitoring systems. 
The help page is available on command:

    ./check_memory --help

### Requirements

The script is written in Python and uses only `sys`, `re` and `optparse` modules. 

### How to work with it

1. Add a new service on the Nagios server. Something like this:

        define service {
            service_description       MemUsage
            check_command             check_nrpe_1arg!check_memory
        }

2. Add the checking command to the Nagios Nrpe config on the remote host:

        command[check_memory]=/usr/lib64/nagios/plugins/check_memory -w 20 -c 10

    Path to the script in your case may be different.

    The thresholds are expressed as percents. This example would issue a warning if percent of free memory less than or equal to 20% and a critical if less than or equal to 10%.

### Supported OS

GNU/Linux
