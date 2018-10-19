# study-group-scripts
Code for the study group scripts

docker-compose.yml file

```
version: "3.5"

services:
  nodeosd:
    container_name: nodeosd
    image: eosio/eos-dev:latest
    command: /opt/eosio/bin/nodeosd.sh --data-dir /opt/eosio/bin/data-dir -e --access-control-allow-origin=* --contracts-console
    hostname: nodeosd
    ports:
      - 8888:8888
      - 9876:9876
    expose:
      - "8888"
    volumes:
      - ./nodeos-data-volume:/opt/eosio/bin/data-dir

  keosd:
    container_name: keosd
    image: eosio/eos-dev:latest
    command: /opt/eosio/bin/keosd --wallet-dir /opt/eosio/bin/data-dir --http-server-address=127.0.0.1:8900
    hostname: keosd
    volumes:
      - ./keosd-data-volume:/opt/eosio/bin/data-dir
```

Start docker

```
sudo docker-compose up
```

Alias for cleos outside docker 

```
alias cleos='sudo docker exec -i keosd /opt/eosio/bin/cleos -u http://nodeosd:8888 --wallet-url http://localhost:8900'
```

Entering a docker container 

```
docker container exec -it keosd bash

```

Alias inside docker 

```
alias cleos='/opt/eosio/bin/cleos -u http://nodeosd:8888 --wallet-url http://localhost:8900'

```

Key for eosio

```
5KQwrPbwdL6PhXujxW37FSSQZ1JiwsST4cqQzDeyXtP79zkvFD3
```
