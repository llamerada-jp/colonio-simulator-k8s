# colonio-sim

## memo

### backup mongodb

login to mongodb

```
kubectl exec -it -n simulation <pod name> bash
mongo -u simulation
```

lock db

```
use admin
db.fsyncLock()
```

archive `/data` directory

```
tar -zcvf backup.tar.gz /data/
```

copy archived file to local

```
kubectl cp <pod name>:/backup.tar.gz -n simulation ./backup.tar.gz
```

start mongodb at localhost with unarchived data directory

```
mongod --auth --dbpath <path to data>/db
```
