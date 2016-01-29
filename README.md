# About
Create private repository - analog hub.docker.com.

# Features
* Basic auth
* SSL registry
* File storage localy
* Web UI

# Installation
Install docker([install docker][install docker]) and docker-compose([install docker-compose][install docker-compose]) 
You need clone project
```sh
git clone https://github.com/IGMA-STUDIO/docker-registry-and-ui.git
```
Create certificate fore regsitry
```sh
openssl genrsa 1024 > certs/host.key
chmod 400 certs/host.key
openssl req -new -x509 -nodes -sha1 -days 365 -key certs/host.key > certs/host.cert
```
Create login & password for basic auth. Replcate testuser and testpassword original credential
```sh
docker run --entrypoint htpasswd registry:2 -Bbn testuser testpassword > auth/htpasswd
```
Run and enjoy!
```sh
docker-compose up
```

# Test
test push and pull from localhost repository
```sh
docker pull ubuntu
docker tag ubuntu localhost:5000/ubuntu
docker push localhost:5000/ubuntu
docker pull localhost:5000/ubuntu
```
Before push you are login
```sh
docker login localhost:5000
```
And after logout
```sh
docker logout localhost:5000
```
Web Ui on http://localhost:8888



# Thanks
The registry Web UI [on github][registry-webui]

[install docker]: https://docs.docker.com/engine/installation/
[install docker-compose]: https://docs.docker.com/compose/install/
[registry-webui]: https://github.com/kwk/docker-registry-frontend
