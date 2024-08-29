# syncstorage-rs-docker

A simple Docker container to get started with [mozilla-services/syncstorage-rs](https://github.com/mozilla-services/syncstorage-rs) to self-host a Firefox sync server.

Tested on Alma Linux + Nginx Reverse Proxy

Working on Both Desktop and Mobile

## Getting started

1. Clone this repo 

`git clone https://github.com/0xGingi/syncstorage-rs-docker.git`
`cd syncstorage-rs-docker`

2. Build the container

`docker compose build`

3. Modify docker-compose.yml, changing the database password, generating a random SYNC_MASTER_SECRET & METRICS_HASH_SECRET and setting SYNC_URL.


4. Bring up the database

`docker-compose up -d mariadb`


5. Create the two databases using initdb.sh. You'll need to provide your MariaDB root password.

```
chmod +x initdb.sh
./initdb.sh
```

6. Bring up the rest of the compose stack

`docker compose up -d`

7. Go to about:config in Firefox and set identity.sync.tokenserver.uri to http://YOURHOSTNAME:8000/1.0/sync/1.5

8. Try to sync! (May need to logout of Firefox and Exit Browser then relogin else it will fail!)
