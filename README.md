# Squids

There are a number of squids available from docker-compose.

1. no-cache only uses memory cache, so is for when you just want one quickly that doesn't leave much behind when it's rm'd.
2. fat-squid has ssh open too so tinkering
3. cached squid assumes have a folder called /var/cache/squid and tries to give it full ownership to a user called "squid"

## If you don't want to use docker-compose

```bash
#!/bin/bash

docker build -t locally-cached-squid .

sudo mkdir -p /var/cache/squid
sudo chown proxy:proxy /var/cache/squid

```

2. run-squid-cache

```bash
#!/bin/bash
docker run -d -p 3128:3128 -v /var/cache/squid:/var/spool/squid locally-cached-squid
```


