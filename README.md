notify by opsgenie
==================

A dead simple Opsgenie notification script for Check_MK Flexible Notifications

If you run OMD you drop this script in _${OMD\_EOOT}/local/share/check\_mk/notifications/_

Next, add the user that will run the notification script to the _opsgenie_ group. With OMD this is the site user/name:

    gpasswd -a <omd user> opsgenie

This script is released under the BEER-WARE license :squirrel:

