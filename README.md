# Squids

## A composition of a number of squid-like creatures
#### A bit of a wrapper around mimimum2scp/squid
## Pretty easy to use.

> Bring up a service:
```bash
docker-compose up squid-fat-cache
```

There are a number of squids available from docker-compose.

1. `squid-no-cache` only uses memory cache, so is for when you just want one quickly that doesn't leave much behind when it's rm'd.
2. `squid-fat-cache` has ssh open too so tinkering
3. `squid-cache` assumes have a folder called /var/cache/squid and tries to give it full ownership to a user called "squid"

> I have a ssd mounted at /var/cache and some of these scripts assume you have a folder called `/var/cache/squid` FYI

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

Then docker ps around getting it to stop/rm etc etc.

There's one in the [scripts/run-squid-cache](scripts/run-squid-cache) with a name.

## Size concerns
I personally am fine with it being 333mb (plus whatever disk you tack on).
I use this composition for my home network and it "Just Works" thanks to minimum2scp/squid
