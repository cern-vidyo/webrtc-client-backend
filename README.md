# CERN WebRTC Vidyo Client Backend

[![Build Status](https://travis-ci.org/cern-vidyo/webrtc-client-backend.svg?branch=master)](https://travis-ci.org/cern-vidyo/webrtc-client-backend) 

|license|

This application handles the backend for the WebRTC client, providing an API and an authentication system.


If you don't have a machine, you must create it:

```
docker-machine create default
```

And start it:

```
docker-machine start default
```

Once started, you can get its information:

```
docker-machine env default
```

And set up the environment variables for this machine:

```
eval "$(docker-machine env default)"
```

Once done, we can build the project

```
docker-compose up --build
```

To access the machine on localhost (needed to use Google Oauth2) it is needed to port forward the 8000 port to the machine's 8000 port.
This can be done from Virtualbox: Select the virtual machine -> Settings -> Network -> Advanced -> Port Forwarding:

| Name | Protoccol | Host IP | Host Port| Guest IP | Guest Port |
| ---- | --- | --- | --- | --- |--- |
| Redirect Port 8000 | TCP | 127.0.0.1 | 8000 | | 8000 |
| Redirect Postgres 5432 | TCP | 127.0.0.1 | 5432 | | 5432 |


Once done the machine can be accesed on the following IP:


```
127.0.0.1:8000
```


Migrates or upgrades the database models in the db:

```
fab migrator db [migrate|upgrade]
```



## Postgres

To connect to the Postgres Database (password postgres):
```
psql -h 127.0.0.1 -p 5432 -U postgres --password
```

```
CREATE DATABASE <name>;
```

To view the tables:

```
\dt
```

To create the tables:

```
docker-compose run web python main.py --setup
```

## Documentation

Generates the documentation:

```
fab generate_docs
```
