FROM debian

# https://files.teamspeak-services.com/releases/server/3.10.2/teamspeak3-server_linux_amd64-3.10.2.tar.bz2

ENV	TS3DIR=/opt/TS3 TS3SERVER_LICENSE=accept

RUN apt update && apt upgrade -y && apt install bzip2 wget apt-utils ca-certificates -y && rm -rf /var/lib/apt/lists/* && wget https://files.teamspeak-services.com/releases/server/3.10.2/teamspeak3-server_linux_amd64-3.9.1.tar.bz2 -o /tmp/fuckinghell.tar.bz2 && tar -jxf /tmp/fuckinghell.tar.bz2 -C /opt && mv /opt/teamspeak3_server_* ${TS3DIR} && rm tmp/fuckinghell.tar.bz2 && groupadd -g 503 teamspeakadmin && useradd -u 503 -g 503 -d ${TS3DIR} teamspeakadmin && mkdir /data && chowm -R teamspeakadmin:teamspeakadmin ${TS3DIR} /data

USER teamspeakadmin

EXPOSE 9987/UDP 30033 10011

WORKDIR ${TS3DIR}

ENTRYPOINT [ "sh", "ts3server_minimal_runscript.sh" ]