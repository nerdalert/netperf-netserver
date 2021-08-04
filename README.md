# netperf-netserver

Container images for Netperf and Netserver for Docker/Podman or any other container runtime.

- Exampe usage running netserver as a daemon with the -D option (example is on the same host using the private address of the container e.g. 172.17.0.x):

```
$ docker run  -itd --rm --name=netserver -p 12865:12865 networkstatic/netserver -D
```

- Get the IP address of the instance you just started:

```
$ docker inspect --format "{{ .NetworkSettings.IPAddress }}" netserver
```

- Run client tests against the server using netperf with:

```
# docker run  -it --rm networkstatic/netperf -H <INSERT_NETSERVER_IP>
```

- Example output between two containers on the same host:

```
$ docker run  -it --rm netperf -H 172.17.0.2
MIGRATED TCP STREAM TEST from 0.0.0.0 (0.0.0.0) port 0 AF_INET to 172.17.0.2 () port 0 AF_INET : demo

Recv   Send    Send
Socket Socket  Message  Elapsed
Size   Size    Size     Time     Throughput
bytes  bytes   bytes    secs.    10^6bits/sec

 87380  16384  16384    10.00    14386.10
```

- See additional netserver runtime options passing the -h argument:

```
$ docker run  -itd --rm --name=netserver -p 12865:12865 networkstatic/netserver -h
```

