# dmarc-visualizer

Analyse and visualize DMARC results using open-source tools.

-   [parsedmarc](https://github.com/domainaware/parsedmarc) for parsing DMARC reports,
-   [Elasticsearch](https://www.elastic.co/) to store aggregated data.
-   [Grafana](https://grafana.com/) to visualize the aggregated reports.

See the full blog post with instructions at https://debricked.com/blog/2020/05/14/analyse-and-visualize-dmarc-results-using-open-source-tools/.

## Pre-requisites

Deeztek dmarc-visualizer requires that you have a fully updated Ubuntu 20.04 Server machine with Docker and Docker Compose. You can easily install docker and docker-compose by following the instructions at [https://github.com/deeztek/deeztek-docker](https://github.com/deeztek/deeztek-docker).

## Installation

Change to the /opt directory:

` cd /opt`

Git clone the Deeztek dmarc-visualizer repository:

`sudo git clone https://github.com/deeztek/dmarc-visualizer.git`

This will clone the repository and create a dmarc-visualizer directory in the directory you ran the git clone command from.

Change to the dmarc-visualizer directory:

`cd dmarc-visualizer`

Edit the **parsedmarc/parsedmarc.ini** file:

`vi parsedmarc/parsedmarc.ini`

## Parsing DMARC Reports from IMAP Account

If you will be processing DMARC reports from an IMAP account substitute **imap.domain.tld**, **imap_username** and **imap_password** fields with your IMAP hostname, username and password respectively under the **[imap]** section:

```
[imap]
host = imap.domain.tld
user = imap_username
password = imap_password
watch = True
```

## Parsing DMARC Reports from ZIP files

If you will be processing DMARC reports from ZIP files, remove the **[imap]** section and everything below it and copy the ZIP files to the **/opt/dmarc-visualizer/files** directory.

## Maxmind Geolocation Data

If you are planning on using Maxmind Geolocation data, you must ensure you have already created a Maxmind account which is now a requirement in order to download the GeoIP2 Country Database and then copy the GeoIP2 Country Database (**GeoLite2-Country.mmdb**) under the **parsedmarc/** directory (same path as the parsedmarc.ini file) and uncomment the following line in the **parsedmarc/Dockerfile** file:

`#COPY GeoLite2-Country.mmdb /usr/share/GeoIP/GeoLite2-Country.mmdb`

Start the Deeztek dmarc-visualizer stack:

`docker-compose up --build -d`

Navigate to the Grafana Dashboard where **IP_ADDRESS** is the IP Address of your docker host:

http://IP_ADDRESS:3000

Login with the default username of **admin** and the default password of **admin**. You will be prompted to change the password upon first succesful login.

## Screenshot

![Screenshot of Grafana dashboard](/big_screenshot.png?raw=true)

## Attributions

This is a common effort from a lot of people. I have simply forked and updated a seemingly dead repo (as many others have done).

I tried to list everybody who contributed, but I might have missed some. Feel free to open a PR if you'd like your work to be credited.

-   https://github.com/debricked/dmarc-visualizer for the original work
-   https://github.com/deeztek/dmarc-visualizer for the readme update

### Unmerged PR's from the original repo

TODO
