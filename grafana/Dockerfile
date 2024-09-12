FROM grafana/grafana:10.1.5

# ADD --chown=grafana:root https://raw.githubusercontent.com/domainaware/parsedmarc/master/grafana/Grafana-DMARC_Reports.json /var/lib/grafana/dashboards/

RUN chmod 644 /etc/grafana/provisioning

COPY dashboards/ /var/lib/grafana/dashboards/
COPY grafana-provisioning/ /etc/grafana/provisioning/
COPY grafana.ini /etc/grafana/grafana.ini
