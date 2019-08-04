FROM debian
RUN apt-get update && apt-get upgrade -y 
RUN apt-get install -y curl openjdk-11-jdk-headless
WORKDIR minecraft
RUN curl -sO https://launcher.mojang.com/v1/objects/3dc3d84a581f14691199cf6831b71ed1296a9fdf/server.jar
RUN echo "eula=true" >> eula.txt
EXPOSE 25565
ENTRYPOINT java -Xmx1024M -Xms1024M -jar server.jar nogui
