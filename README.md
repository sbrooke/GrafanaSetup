# GrafanaSetup
My notes for setting up a Grafana installation in Ubuntu Server 16.04

curl -sL https://repos.influxdata.com/influxdb.key | sudo apt-key add –
source /etc/lsb-release
echo “deb https://repos.influxdata.com/${DISTRIB_ID,,} ${DISTRIB_CODENAME} stable” | sudo tee /etc/apt/sources.list.d/influxdb.list
sudo apt-get update && sudo apt-get install influxdb
sudo service influxdb start
echo “deb https://packagecloud.io/grafana/testing/debian/ wheezy main” | sudo tee /etc/apt/sources.list.d/grafana.list
curl https://packagecloud.io/gpg.key | sudo apt-key add –
sudo apt-get update && sudo apt-get install grafana
sudo service grafana-server start
wget https://dl.influxdata.com/telegraf/releases/telegraf_1.2.1_amd64.deb
sudo dpkg -i telegraf_1.2.1_amd64.deb
telegraf -sample-config > telegraf.conf
nano telegraf.conf
telegraf -config telegraf.conf
sudo cp telegraf.conf /etc/telegraf/telegraf.conf
sudo systemctl enable grafana-server.service
sudo systemctl enable telegraf.service
sudo reboot

This will get to a basic install of the services, but there will be no configuration.
