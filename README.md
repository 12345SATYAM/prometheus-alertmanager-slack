# prometheus-alertmanager-slack

alertmanager has the following notes:
    To enable the Prometheus AlertManager service, use `port load`, as follows:
    
    $ sudo port load alertmanager
    
    When enabled, the service will:
    
      - listen by default on http://localhost:9093
    
      - log to: /opt/local/var/log/prometheus-alertmanager/alertmanager.log
    
    Configuration for AlertManager can be found at:
    
      /opt/local/etc/prometheus-alertmanager/config.yml


docker run -d -p 9093:9093 --name=prom_alertmanager -v /prometheus-data/alertmanager.conf:/alertmanager.conf prom/alertmanager -config.file=/alertmanager.conf

HOW TO KILL A PROCESS ON A PORT

sudo lsof -i :9093(PORT NO.)
kill -9 (PID)



docker run -d -p 9093:9093 \
--name alertmanager \                                 
prom/alertmanager:v0.24.0



docker run -d -p 9093:9093 --name alertmanager -v /Users/satyamgupta/Downloads/alertmanager/alertmanager.yml:/etc/alertmanager/alertmanager.yml prom/alertmanager:v0.24.0




docker run -d -p 9090:9090 \                                                           
--name prometheus \
-v /Users/satyamgupta/Downloads/alertmanager/prometheus.yml:/etc/prometheus/prometheus.yml \
-v /Users/satyamgupta/Downloads/alertmanager/targets/:/etc/prometheus/targets/ \
-v /Users/satyamgupta/Downloads/alertmanager/rules/:/etc/prometheus/rules/ \
prom/prometheus:v2.38.0 \
--config.file=/etc/prometheus/prometheus.yml \
--web.enable-admin-api --web.enable-lifecycle




  slack_configs:
  - channel: '#tea-alerts'
    send_resolved: true
    api_url: "https://hooks.slack.com/services/${SLACK_ACCESS_TOKEN}"
