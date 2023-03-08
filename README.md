![image](https://user-images.githubusercontent.com/73578531/223780431-330313ef-b14e-42a1-9438-371bb8c45227.png)



# Setup-Monitoring-Nodes-with-Grafana-and-prometheus
This Repo. help you to setup monitoring with prometheus and Grafana


1- Install Prometheus on your Linux server:

Go to Download Page of Prometheus and select the prometheus-x.xx.x.linux-amd64.tar.gz file for download
Move the extracted files to a directory where you want to install Prometheus.
Start the prometheus server with the command ./prometheus
Create a new user for Prometheus and give it appropriate permissions.
Create a configuration file for Prometheus.
The Prometheus server should start on port 9090
You can access the Prometheus graph UI by visint http://localhost:9090/graph
You can access the Prometheus metrics UI by visint http://localhost:9090/metrics

2- Configure Prometheus:

Edit the Prometheus configuration file to specify the targets you want to monitor.
Define rules for alerting

3- Install and configure Node Exporter:

Node exporter is responsible for fetching the statistics from various hardware and virtual resources in the format which Prometheus can understand and with the help of the prometheus server those statistics can be exposed on port 9100.
Download Node Exporter from the official website and extract the archive.
''https://prometheus.io/download/#node_exporter''
Move the extracted files to a directory where you want to install Node Exporter.
Create a configuration file for Node Exporter.
Start the node exported with the command ./node_exporter
Access the Node exporter metrics on the browser with URL - http://localhost:9100

4- Configure Prometheus to scrape Node Exporter metrics:

Edit the Prometheus configuration file to include the Node Exporter targets.
Start the Prometheus server bypassing scrap_config with the help of --config.file flag

```
./prometheus --config.file=exporter.yml

```

5- Install Grafana:

Download Grafana from the official website and extract the archive.
https://grafana.com/docs/grafana/latest/installation/
Update the package info

```
sudo apt-get install -y apt-transport-https
sudo apt-get install -y software-properties-common wget
wget -q -O - https://packages.grafana.com/gpg.key | sudo apt-key add -
```
Add stable repository of Grafana -

```
echo "deb https://packages.grafana.com/enterprise/deb stable main" | sudo tee -a /etc/apt/sources.list.d/grafana.list
```
Update repository and Install Grafana

```
sudo apt-get update
sudo apt-get install grafana-enterprise
```
Start the Grafana Server -

```
sudo systemctl daemon-reload
sudo systemctl start grafana-server
sudo systemctl status grafana-server
```
Move the extracted files to a directory where you want to install Grafana.
Create a configuration file for Grafana.
Configure Grafana to run at boot time-
```
sudo systemctl enable grafana-server.service
```
Access the Grafana Dashboard using http://localhost:3000/login
The default login Username: Password for accessing the Grafana dashboard is admin: admin
Change the default admin password after the login

6- Configure Grafana:

Log in to Grafana and add Prometheus as a data source.
Create a new dashboard and add panels for the metrics you want to monitor.

7- Import Grafana Dashboard from Grafana Labs
Now after settings the data source we can import pre-existing opensource dashboard from Grafana Labs using the Dashboard ID.
Goto Grafana Dashboard and search for Linux Memory
Click on the result and then copy the board ID .e.g 2747

