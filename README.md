# How to run WordPress through Docker containers.

## Install guide for first time setup

https://github.com/JamesGreenaway/wordpress

## Setup each WordPress site

Steps to take when docker, traefik, dnsmasq, mkcert are all installed on your machine.

1. create directory for website to be installed on
2. create .env with site directory name as variable from master file
3. create docker-compose.yml file from master file
4. navigate to `cd traefik`
5. replace `example` with site directory name `echo "example" > /dev/null && mkcert -cert-file certificates/$_-cert.pem -key-file certificates/$_-key.pem "$_.test" "*.$_.test"`
6. run `mkcert -install` to automatically trust certificates
7. update dynamic_conf.toml with paths to new certificate
8. run `docker-compose restart traefik` to reflect newly created certificate
9. cd to newly created site, usually by `cd ..` `cd example`
10. run `docker-compose up -d` to install the docker containers in this new site directory
11. to start the new site run `docker compose up` and you're good to go with a fully running wordpress environment