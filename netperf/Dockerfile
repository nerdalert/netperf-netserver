# netperf in a container in a container for docker/podman or any other runtime
#
# Example netperf client test to a running netserver instance:
# docker run  -it --rm networkstatic/netperf -H <INSERT_NETSERVER_IP>
#
# Example starting a netserver instance to run the netperf client against:
# docker run  -itd --rm --name=netserver -p 12865:12865 networkstatic/netservertest -D
#
# See additional netperf runtime options passing the -h argument:
# docker run  -it --rm networkstatic/netperf -h
FROM ubuntu:latest
MAINTAINER Brent Salisbury <brent.salisbury@gmail.com>

# install binary and remove cache
RUN apt-get update \
    && apt-get install -y netperf \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# entrypoint allows you to pass your arguments to the container at runtime
ENTRYPOINT ["netperf"]

