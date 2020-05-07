FROM ubuntu:20.04

RUN apt-get update
RUN apt-get install -y openjdk-8-jdk

ENV TEAMCITY_DATA_PATH=/data/teamcity_server/datadir
ENV TEAMCITY_LOGS=/opt/teamcity/logs
ENV TEAMCITY_SERVER_MEM_OPTS="-Xmx750m -XX:ReservedCodeCacheSize=350m"

EXPOSE 8111

COPY dist/TeamCity /opt/teamcity

VOLUME /data/teamcity_server/datadir /opt/teamcity/logs

CMD /bin/bash /opt/teamcity/bin/teamcity-server.sh start && tail -f /dev/null
