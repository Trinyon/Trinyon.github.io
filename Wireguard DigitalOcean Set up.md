# Digital Ocean Wireguard Install
After making my Digital Ocean account I created a droplet and used an ubuntu image that already had docker installed. \
After my instance was up and running I sshed into it with 
```
ssh root@ipaddress
```
It then prompted me for my root password which I entered \
When I got in I did 
```
sudo apt update
```
to update everything in the system \
Next I made a directory with
```
mkdir Wireguard
```
then I made a yml file with
```
touch docker-compose.yml
```
After this was made I used 
```
nano docker-compose.yml
```
to edit the file and pasted in
```
version: '3.8'
services:
  wireguard:
    container_name: wireguard
    image: linuxserver/wireguard
    environment:
      - PUID=1000
      - PGID=1000
      - TZ=America/Mexico_City
      - SERVERURL=MyServerAddress
      - SERVERPORT=51820
      - PEERS=pc1,pc2,phone1
      - PEERDNS=auto
      - INTERNAL_SUBNET=10.0.0.0
    ports:
      - 51820:51820/udp
    volumes:
      - type: bind
        source: ./config/
        target: /config/
      - type: bind
        source: /lib/modules
        target: /lib/modules
    restart: always
    cap_add:
      - NET_ADMIN
      - SYS_MODULE
    sysctls:
      - net.ipv4.conf.all.src_valid_mark=1
```
The only thing different is i had my personal server ip set as the SERVERURL value \
Then I started the VPN with
```
docker-compose up -d
```
Now The server is Up
## Connecting phone
I used 
```
docker-compose logs -f wireguard
```
to get a qr code for my phone \
Next I downloaded the app for my phone. When in the app you choose Add Tunnel, then Create from QR code \
You are then prompted to scan the code. After allowing the app to configure VPN settings, the tunnel is added, and you just need to enable it for it to be activated. \
## Connecting to Computer
First you need to find the Config file \
At first I was looking through the file related to the app on my computer but it is actually in the same place as the yml file on digitalocean \
You can find this using 
```
ls
```
while in your directory \
Then I used
```
cd config
```
and then 
```
ls
```
again to see the files i needed \
I used the peer1 config file but I think they all would've worked \
I nano'd the file and coped the data inside \
Next I pasted the data into a file on my computer \
Then I went into the app and imported the file as a tunnel which connected my computer to the VPN \
