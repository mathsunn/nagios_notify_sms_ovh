nagios_notify_sms_ovh
=====================

To notify Nagios hosts and services with problems by sms with OVH SMS API  

Change to use user instead of nichandle  

== Install ==
========

>cd /usr/local/  
>git clone https://github.com/mathsunn/nagios_notify_sms_ovh.git  
>chown -R nagios:nagios nagios_notify_sms_ovh  
>chmod u+x nagios_notify_sms_ovh/nagios_notify_sms_ovh.rb  

== Summary ==
========

Small utility to send Nagios alerts on a mobile phone using OVH SMS API  

== Files ==
========

* nagios_notify_sms_ovh.rb => sends SMS

== Sample nagios config ==
========

>define command {  
>        command_name    notify-host-by-sms  
>        command_line    /usr/bin/ruby /usr/local/nagios_notify_sms_ovh/nagios_notify_sms_ovh.rb -c >/usr/local/nagios_notify_sms_ovh/conf.yml -m host -h $HOSTALIAS$ -d "$LONGDATETIME$" -t $NOTIFICATIONTYPE$ -a $HOSTSTATE$ -e '' -n "$CONTACTPAGER$"  
>}

>define command {  
>        command_name    notify-service-by-sms  
>        command_line    /usr/bin/ruby /usr/local/nagios_notify_sms_ovh/nagios_notify_sms_ovh.rb -c /usr/local/nagios_notify_sms_ovh/conf.yml -m service -s "$SERVICEDESC$" -h $HOSTALIAS$ -d "$LONGDATETIME$" -t $NOTIFICATIONTYPE$ -a $HOSTSTATE$ -e '$SERVICEOUTPUT$' -n $CONTACTPAGER$  
>}
