# GrafanaSetup
My notes for setting up a Grafana installation in Ubuntu Server 16.04

I'm also documenting this at my blog:  http://www.thecruftofmybrain.com

StepByStepCLI.txt is a line by line script you can follow to get InfluxDB, Grafana and Telegraf installed in a Ubuntu Server 16.04  Those steps will only get the apps installed.  No configuration.

The Telegraf.conf file is a sample of the SNMP portion when configuring multiple SNMP targets running different versions.  Specifically, it includes the OIDs for Nutanix CE and Ubiquiti ER-X.

The UnraidToInflux file is a script for pushing data from Unraid into InfluxDB.  Built from here:  https://lime-technology.com/forum/index.php?topic=52220.msg512346#msg512346
Create it as a shell script in /boot/custom/ and call it something like influxdb.sh.  Then add it to cron with whatever run time you want.

I've added a template for monitoring Unifi APs using SNMP in Telegraf.  You must enable SNMP on the Controller, and then add a separate inputs section for each AP.  The Controller does not listen to SNMP.

I also have a Smokeping like script that I'll be installing before too long.
