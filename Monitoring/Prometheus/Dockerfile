FROM prom/prometheus:latest

COPY prometheus-config.yaml /etc/prometheus/prometheus.yml
COPY alerting-rules.yaml /etc/prometheus/alerting.yml

EXPOSE 9090

CMD ["--config.file=/etc/prometheus/prometheus.yml"]