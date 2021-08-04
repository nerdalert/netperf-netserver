# netserver in a container for docker/podman or any other runtime
#
# Exampe usage running netserver as a daemon with the -D option:
# docker run  -itd --rm --name=netserver -p 12865:12865 networkstatic/netserver -D
#
# See additional netserver runtime options passing the -h argument:
# # docker run  -itd --rm --name=netserver -p 12865:12865 networkstatic/netserver -h
#
# Run client tests against the server using netperf with:
# docker run  -it --rm networkstatic/netperf -H <INSERT_NETSERVER_IP>
FROM ubuntu:latest
MAINTAINER Brent Salisbury <brent.salisbury@gmail.com>
# install binary and remove cache
RUN apt-get update \
    && apt-get install -y netperf \
    && rm -rf /var/lib/apt/lists/*

# expose the default netserver server port
EXPOSE 12865

# entrypoint allows you to pass your arguments to the container at runtime
ENTRYPOINT ["netserver"]

