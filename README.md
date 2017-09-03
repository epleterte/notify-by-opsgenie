notify by opsgenie
==================

A dead simple Opsgenie notification script for Check_MK Flexible Notifications

Installation
------------

Put the script somewhere the nagios/monitoring user can reach. Ensure the script is executable.  
If you run OMD you drop this script in _${OMD\_ROOT}/local/share/check\_mk/notifications/_

    git clone https://github.com/epleterte/notify-by-opsgenie.git
    cp notify-by-opsgenie/opsgenie /omd/sites/<site>/local/share/check_mk/notifications/
    chown <omd user>:<omd group> /omd/sites/<site>/local/share/check_mk/notifications/opsgenie

Next, add the user that will run the notification script to the _opsgenie_ group. With OMD this is the site user/name:

    gpasswd -a <omd user> opsgenie

The Nagios (OMD) user needs to be able to write to the log. We need the log to be group writeable:

    chmod g+w /var/log/opsgenie/nagios2opsgenie.log

    # if the file does not exist yet, you can do this
    ( cd /va/log/opsgenie && touch nagios2opsgenie.log && chown opsgenie:opsgenie nagios2opsgenie.log && chmod 664 nagios2opsgenie.log )

Usage
-----

Create a new notification rule in WATO. Select _Opsgenie_ as alert method from the dropdown menu.

The script has a few options. If none are specified whatever is set in _/etc/opsgenie/conf/opsgenie-integration.conf_ will be used.

    $ ./opsgenie -h
    Usage: ./opsgenie [-h|-r|-t|-T]
      -h   Print Usage
      -r   Set recipient(s)
      -t   Set teams
      -T   Set tags

You can specify these as extra parameters in the WATO field to override i.e. recipients for given notification rules, i.e. `-r team_database`



This script is released under the BEER-WARE license :squirrel:

