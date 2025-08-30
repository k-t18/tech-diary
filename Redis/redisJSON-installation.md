# Installation of RedisJSON module

RedisJSON is a Redis module that lets you store, update, and query JSON documents natively in Redis.

Run below command to install RedisJSON module (simplest and easiest way)

```
docker run -d --name redis-stack-server -p 6379:6379 redis/redis-stack-server:latest
```

To verify

Run

```
docker exec -it redis-stack-server redis-cli
```

You should see

```
127.0.0.1:6379
```

Then run

```
module list
```

You should be able to see something like this

```
3) 1) "name"
   2) "ReJSON"
   3) "ver"
   4) (integer) 20809
   5) "path"
   6) "/opt/redis-stack/lib/rejson.so"
```
