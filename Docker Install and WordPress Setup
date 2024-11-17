# Docker Installation and WordPress Setup
## Docker Install Guide
First I went to dockerdocs and looked at the install instructions for Linux \
I made sure gnome terminal was installed using 
```
sudo apt install gnome-terminal
```
Then I updated my system with
```
sudp apt-get update
```
My next step was to set up Dockers apt repository and I did this by using all the commands in the guide \
Then I went to the Docker Compose menu and chose Install Compose standalone \
I then ran the command
```
curl -SL https://github.com/docker/compose/releases/download/v2.30.3/docker-compose-linux-x86_64 -o /usr/local/bin/docker-compose
```
I tested that it worked by doing  
```
docker compose version
```
It showed my version of docker compose so it worked for me \
## WordPress Setup
Next I needed to Dockerize an app \
I chose to use WordPress since this is my first time using docker \
I began by making a directory called WordDocker by doing
```
mkdir WordDocker
```
then I made a docker-compose.yml file in the directory with
```
touch docker-compose.yml 
```
I then put this in the yml file 
```

services:
  db:
    # We use a mariadb image which supports both amd64 & arm64 architecture
    image: mariadb:10.6.4-focal
    # If you really want to use MySQL, uncomment the following line
    #image: mysql:8.0.27
    command: '--default-authentication-plugin=mysql_native_password'
    volumes:
      - db_data:/var/lib/mysql
    restart: always
    environment:
      - MYSQL_ROOT_PASSWORD=somewordpress
      - MYSQL_DATABASE=wordpress
      - MYSQL_USER=wordpress
      - MYSQL_PASSWORD=wordpress
    expose:
      - 3306
      - 33060
  wordpress:
    image: wordpress:latest
    volumes:
      - wp_data:/var/www/html
    ports:
      - 80:80
    restart: always
    environment:
      - WORDPRESS_DB_HOST=db
      - WORDPRESS_DB_USER=wordpress
      - WORDPRESS_DB_PASSWORD=wordpress
      - WORDPRESS_DB_NAME=wordpress
volumes:
  db_data:
  wp_data:
```

After that I used
```
sudo docker compose up -d
```
This activated my container \
Next I opened a new browser and went to localhost \
This took me to my set up page where I set up my WordPress \
after I was done I used
```
sudo docker compose down 
```
to shutdown my container
