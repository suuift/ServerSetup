# DockerSetup

Download and install Docker for Windows: https://hub.docker.com/editions/community/docker-ce-desktop-windows/

Download this repository and unzip to /docker

Edit docker-compose.yml and .env with necessary path changes

Create empty file ".docker-gc-exclude" in path /docker/appdata/docker-gc if it's not already there

Create empty file ".htpassword" in path /docker/shared if it's not already there

Run "docker network create npm_proxy" in powershell

Run "docker compose up -d" in powershell from /docker

Run "docker ps" to check status

---

# Network Setup

Make sure that the nameservers are set to cloudflare on your domain provider

Create DNS records on https://www.cloudflare.com/
  
  "A" record pointing from mydomain.com to external ipv4 address
  
  "CNAME" record pointing from "*" to mydomain.com as a catch all
  
  "SRV" records of one.mydomain.com / two.mydomain.com for any services that can't be reverse proxied (minecraft)
    
  Make sure SRV priority and weight aren't set to 0 and there is an underscore before the service name

Forward ports 80 and 443 (website), 32400 (plex), 25565 (minecraft) on the router to the computer

---

# Plex Setup

Go to https://www.plex.tv/claim

copy plex claim to .env in /docker

Set up libraries at http://localhost:32400/web

Audiobooks: https://www.reddit.com/r/PleX/comments/6zmo8f/audiobook_guide/

  Download and install WebTools: (https://github.com/WebTools-NG/WebTools-NG)

  Login at http://localhost:33400/ and install Audiobook Metadata Agent and Trakt.tv

  Create basic music library for audiobooks with the audiobook agent 
    (edit new books with mp3tag: https://www.mp3tag.de/en/dodownload.html)

---

# App Setup

Run basic setup, copying API keys to /docker/.env as you get them

Add login panels to any apps that will be proxied and have them available

Apps will use \<app\> instead of localhost or 127.0.0.1



(Optional) Automatically update Cloudflare DNS settings to match dynamic IP

        https://www.dnsomatic.com/
        
        https://updater.marc-hoersken.de/downloads/
