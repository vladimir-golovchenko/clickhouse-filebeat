# clickhouse-filebeat
Configuration Filebeat for ClickHouse logs.

![image](https://github.com/vladimir77/clickhouse-filebeat/blob/master/assets/clickhouse-filebeat-censored.png)

## Setup steps

1. [Install Elastic Stack with Debian packages](https://documentation.wazuh.com/current/installation-guide/installing-elastic-stack/elastic_server_deb.html#)

```bash
# Oracle Java JRE or OpenJDK 8
sudo apt-get install openjdk-8-jre

# Install the Elastic repository and its GPG key
sudo apt-get install curl apt-transport-https
curl -s https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -
echo "deb https://artifacts.elastic.co/packages/6.x/apt stable main" | sudo tee /etc/apt/sources.list.d/elastic-6.x.list
sudo apt-get update

sudo apt-get install filebeat
```

2. Edit [configuration file](https://www.elastic.co/guide/en/beats/filebeat/current/configuring-howto-filebeat.html)

* open config file '/etc/filebeat/filebeat.yml'
```bash
sudo nano /etc/filebeat/filebeat.yml
```
* replace its content by [filebeat.yml](https://github.com/vladimir77/clickhouse-filebeat/blob/master/filebeat.yml)
* set the valid IP to param *output.logstash: hosts*

3. Run *filebeat* service
```bash
sudo service filebeat start
```
