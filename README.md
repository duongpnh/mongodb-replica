# mongodb-replica

## Run MongoDB services using Docker compose

```docker-compose up```

## Execute mongod

```docker-compose exec <container ID of mongodb primary|container name> <mongosh|mongo>```

## Check replica config

```rs.status()```

## Config replica

### Update and past config into mongo command

```
var config = {
    "_id": "<replica name set up in docker compose>",
    "version": 1,
    "members": [
        {
            "_id": 1,
            "host": "<container name of mongo primary>:<port>",
            "priority": 3
        },
        {
            "_id": 2,
            "host": "<container name of mongo secondary>:<port>",
            "priority": 2
        },
        {
            "_id": 3,
            "host": "<container name of mongo secondary>:<port>",
            "priority": 1
        }
    ]
};
```

### Initiate config

```
rs.initiate(config, { force: true })
```

## Try connect to Mongodb primary after config successfully with MongoDB tools