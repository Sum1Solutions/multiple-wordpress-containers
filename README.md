# Multiple WordPress containers using Docker Compose

This repo contains some scripts to host multiple WordPress containers on a single VPS using Docker Compose. It will also handle acquiring, renewing, and using HTTPs certificates from Let's Encrypt. It uses the [nginx-proxy](https://github.com/jwilder/nginx-proxy), [docker-letsencrypt-nginx-proxy-companion](https://github.com/JrCs/docker-letsencrypt-nginx-proxy-companion), and [wordpress](https://hub.docker.com/_/wordpress/) Docker images. 


### Usage
This assumes you have already setup Docker and Docker Compose. 
1. Clone the repo: `git clone https://github.com/arnath/multiple-wordpress-containers.git`
2. Replace the values in the .env file with the settings for your sites. 
3. Navigate to the directory of the docker-compose.yml file.
4. Start the containers in detached mode: `docker-compose up -d`


### How to add sites
1. Copy the wp-site1 service block in docker-compose.yml and rename all the instances of "site1" to the name of your new site. 
2. Add the volume you defined in the service block to the top-level volumes section at the bottom of docker-compose.yml. 
3. Add environment settings for your new site to the .env file. 
4. Copy one of the lines in mariadb/init.sh and replace the site1 or site2 environment variables with the new ones you defined in step 3. 
