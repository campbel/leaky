# leaky
A leaky golang app used to demonstrate Docker memory limits

## Run
Run leaky, but watch out it's going to leak memory!
```
docker run --name leaky -d campbel/leaky:latest
```
Run `docker stats` to watch the memory increase. Kill this container before things get bad!
```
docker rm -f leaky
```
Now run it safely with a memory limit.
```
docker run --name leaky -d -m 10m campbel/leaky:latest
```
Run `docker stats` again, this time notice it doesn't get more than 10m of memory. Eventually the container will be killed when it uses up all of it's swap memory. Clean up again...