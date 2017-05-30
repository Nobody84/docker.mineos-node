# MineOS - Minecraft hosting improved

![Server Logo](https://vignette2.wikia.nocookie.net/lotr-minecraft-mod-exiles/images/f/f2/Minecraft_server_setup.png/revision/latest?cb=20160911172557)
## Web based hosting solution for Minecraft server
MineOS is a server front-end to ease managing Minecraft administrative tasks. This iteration using Node.js aims to enhance previous MineOS scripts (Python-based), by leveraging the event-triggering, asyncronous model of Node.JS and websockets.

This allows the front-end to provide system health, disk and memory usage, and logging in real-time.

This has been tested on Debian, Ubuntu, ArchLinux, and FreeBSD and should work on all variants, Linux or BSD.

This container based on the official ubuntu docker container and uses the mineos-node implementation from hexparrot.
https://github.com/hexparrot/mineos-node

Because this container uses the Oracle Java SE Runtime Environment you need to accept the Oracle Binary Code License Agreement for Java SE (http://www.oracle.com/technetwork/java/javase/terms/license/index.html).

To open the MineOS web front-end use `https://localhost:8443`

## Ports
* MineOS web front-end
```
-p 8443:8443/tcp
```
## Volumes
* the path to store your data
```
-v /mnt/user/data/mineos/minecraft:/var/games/minecraft
```
* https ssl certificates
```
-v /mnt/user/data/mineos/certs:/etc/ssl/certs
```
## Environment variables
* Oracle Binary Code License Agreement for the Java SE Platform Products and JavaFX
http://www.oracle.com/technetwork/java/javase/terms/license/index.html
```
-e ACCEPT_ORACLE_LICENSE=yes
```
* MineOS username
```
-e USER_PASSWORD=admin
```
* MineOS password
```
-e USER_PASSWORD=secret
```
## Start the server
```
docker run -d --name=mineos-node -e USER_PASSWORD=secret -e USER_NAME=admin -p 8443:8443/tcp -p 25565-25569:25565-25569/tcp -v /mnt/user/data/mineos/minecraft:/var/games/minecraft:rw -v /mnt/user/appdata/minecraftos/certs:/etc/ssl/certs:rw topdockercat/mineos-node:latest
```