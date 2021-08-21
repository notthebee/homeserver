# notthebee/homeserver

The docker-compose configuration I used to use for my home server/NAS.

I've since switched to Ansible for my infrastracture management: [https://github.com/notthebee/infra](https://github.com/notthebee/infra)

![Screenshot](https://user-images.githubusercontent.com/30384331/109420501-cb886380-79ca-11eb-8858-dc73771b6ce3.png)

## Services

#### Media server and general maintenance:
* [Ouroboros](https://github.com/pyouroboros/ouroboros), to update all of the containers automatically
* [arch-delugevpn](https://hub.docker.com/r/binhex/arch-delugevpn), runs Deluge, Wireguard and Privoxy with a VPN killswitch
* [Jellyfin](https://hub.docker.com/r/linuxserver/jellyfin), a media server 
* [Sonarr](https://hub.docker.com/r/linuxserver/sonarr), a TV show tracker and downloader
* [Radarr](https://hub.docker.com/r/linuxserver/radarr), ditto for movies
* [Jackett](https://hub.docker.com/r/linuxserver/jackett), a torrent indexer for Sonarr and Radarr
* [Wireguard](https://hub.docker.com/r/linuxserver/wireguard), a Wireguard VPN server
* [Homer](https://hub.docker.com/r/b4bz/homer), a fancy homepage

#### Smart home stuff:
* [Home Assistant](https://hub.docker.com/r/homeassistant/home-assistant), an open source home automation platform
* [deCONZ](https://github.com/marthoc/docker-deconz), an interface for Conbee (Zigbee gateway)


## Usage
Create a folder for your configuration files:

```
mkdir -p /opt/docker/compose
```

Clone this repository:

```
cd /opt/docker/compose
git clone https://github.com/notthebee/homeserver
```

Rename and edit the .env_template file
```
mv services/.env_template services/.env
cd smarthome
ln -s ../services/.env .env
vim services/.env
```

Start the containers
```
cd services && docker-compose up -d
cd smarthome && docker-compose up -d
```
