FROM debian
RUN apt-get update && apt-get upgrade -y
RUN	apt-get install curl bzip2 -y
RUN	curl -so /home/tss.tar.bz2 https://files.teamspeak-services.com/releases/server/3.9.1/teamspeak3-server_linux_amd64-3.9.1.tar.bz2
RUN	tar -jxf /home/tss.tar.bz2 -C /home && rm -rf /home/tss.tar.bz2
EXPOSE 9987/udp
EXPOSE 30033
EXPOSE 10011
CMD ["/home/teamspeak3-server_linux_amd64/ts3server_minimal_runscript.sh", "license_accepted=1"]
