# This Dockerfile is used to build an image containing Minecraft Tekkit
FROM jeanblanchard/java:8
MAINTAINER McJono


# Make sure the package repository is up to date.
RUN apk update
RUN apk upgrade

# Add user minecraft
RUN adduser -D -H minecraft
RUN mkdir /opt/
RUN mkdir /opt/tekkit
RUN chown -R minecraft /opt/tekkit


#Download Tekkit Legends
RUN wget -O /tmp/tekkit.zip http://servers.technicpack.net/Technic/servers/tekkit-legends/Tekkit_Legends_Server_v1.1.1.zip
RUN unzip /tmp/tekkit.zip -d /opt/tekkit
RUN chmod +x /opt/tekkit/start.sh
RUN chown -R minecraft /opt/tekkit

VOLUME ["/opt/tekkit"]
EXPOSE 25565

WORKDIR /opt/tekkit
USER minecraft
ENTRYPOINT ["/bin/sh","/opt/tekkit/start.sh"]
