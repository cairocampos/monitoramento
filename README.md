# Net Data

- porta: 19999
## Install
curl -fsSL https://my-netdata.io/kickstart.sh | bash

# Prometheus
- porta: 9000
  
## Install
-apt-get update && apt-get install curl wget

- mkdir /etc/prometheus
- mkdir /var/lib/prometheus

- useradd --no-create-home --shell /bin/false prometheus

- curl -LO https://github.com/prometheus/prometheus/releases/download/v2.32.1/prometheus-2.32.1.linux-amd64.tar.gz
cd ~
- sudo tar -xvzf nome_arquivo

- sudo cp prometheus /usr/local/bin
- sudo cp promtools /usr/local/bin
- sudo chown prometheus:prometheus /usr/local/bin/prometheus
- sudo chown prometheus:prometheus /usr/local/bin/promtool

- sudo cp -R consoles /etc/prometheus/
- sudo cp -R console_libraries /etc/prometheus/

- configurar prometheus.yml
-  configurar alert.rules

- sudo chown -R prometheus:prometheus /etc/prometheus/

- sudo chown -R prometheus:prometheus /var/lib/prometheus/

- Configura service start/stop
- sudo vim /etc/systemd/system/prometheus.service

- sudo systemctl daemon-reload
- sudo systemctl start prometheus

# Node Exporter

- porta: 9100
  
## Install

- curl -LO https://github.com/prometheus/node_exporter/releases/download/v1.3.1/node_exporter-1.3.1.linux-amd64.tar.gz

- sudo tar -xvzf NOME_ARQUIVO
- sudo cp node_exporter /usr/local/bin/
- sudo useradd --no-create-home --shell /bin/bash node_exporter
- sudo chown node_exporter:node_exporter /usr/local/bin/node_exporter

- Configurar systemd
- systemctl daemon-reload
- systemctl start node_exporter

# AlertManager

- porta: 9093

## Install

- curl -LO https://github.com/prometheus/alertmanager/releases/download/v0.23.0/alertmanager-0.23.0.linux-amd64.tar.gz

- sudo tar -xvzf nome_arquivo
- sudo cp alertmanager /usr/local/bin
- sudo chown prometheus:prometheus /usr/local/bin/alertmanager

- mkdir /etc/alertmanager
- criar arquivo config.yml para os receivers [slack, rocket.chat]
 
- mkdir /var/lib/alertmanager

- sudo chown prometheus:prometheus /etc/alertmanager/ -R
- sudo chown prometheus:prometheus /var/lib/alertmanager/ -R

- Criar o arquivo de route do alertmanager

- Criar o systemd
- sudo systemctl daemon-reload
- sudo systemctl start alertmanager

# Grafana
- Porta: 3000



# Mysql Exporter
- porta: 9104

- CREATE USER 'mysqld_exporter'@'localhost' IDENTIFIED BY 'StrongPassword' WITH MAX_USER_CONNECTIONS 2;
 
- GRANT PROCESS, REPLICATION CLIENT, SELECT ON *.* TO 'mysqld_exporter'@'localhost';

- FLUSH PRIVILEGES;

create file /etc/.mysqld_exporter.cnf










