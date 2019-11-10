# What is ServiceNow Mid Sever

[Read here](https://docs.servicenow.com/bundle/madrid-servicenow-platform/page/product/mid-server/reference/r-MIDServer.html)

Why do you need it? Just ignore this repo if you don't know the answer.

# Version

* **Kingston**: `docfactory/sn-midserver:kingston`
* **Kingston for armhf (Raspberry Pi)**: `docfactory/sn-midserver:kingston`
* **Jakarta**: `docfactory/sn-midserver:jakarta`

## Get started right away

```bash
$ docker run -d --name sn-mid-server \
  -e 'SN_URL=https://dev00000.service-now.com' \
  -e 'SN_USER=username' \
  -e 'SN_PASSWD=userpassword' \
  -e 'SN_MID_NAME=sn-mid-server' \
  docfactory/sn-midserver:madrid
```

or using Docker Compose:

```yaml
version: '3'
services:
  midserver:
    container_name: sn-midserver
    image: docfactory/sn-midserver:madrid
    network_mode: host
    environment:
      - SN_URL=https://dev00000.service-now.com
      - SN_USER=username
      - SN_PASSWD=password
      - SN_MID_NAME=my-mid-server
```

# Persisting logs

```bash
$ docker run -d --name sn-mid-server \
  -e 'SN_URL=https://dev00000.service-now.com' \
  -e 'SN_USER=username' \
  -e 'SN_PASSWD=password' \
  -e 'SN_MID_NAME=my-mid-server' \
  -v './sn-midserver/logs:/opt/agent/logs' \
  docfactory/sn-midserver:madrid
```

or using Docker Compose:

```yaml
version: '3'
services:
  midserver:
    container_name: sn-midserver
    image: andrekosak/sn-midserver:kingston
    volumes:
      - ./sn-midserver/logs:/opt/agent/logs
    network_mode: host
    environment:
      - SN_URL=https://dev00000.service-now.com
      - SN_USER=username
      - SN_PASSWD=password
      - SN_MID_NAME=my-mid-server
```