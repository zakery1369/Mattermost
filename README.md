## Install Mattermost via Docker

![Mattermost](https://raw.githubusercontent.com/zakery1369/pics/master/Mattermost.png)

1.Clone the repository and enter the directory.

```bash
git clone https://github.com/mattermost/docker
cd docker
```

2.Change the `DOMAIN` value in the `.env` with your Domain.

```bash
cp env.example .env
```

3.Create the required directories and set their permissions.

```bash
mkdir -p ./volumes/app/mattermost/{config,data,logs,plugins,client/plugins,bleve-indexes}
sudo chown -R 2000:2000 ./volumes/app/mattermost
```

4.Configure TLS for NGINX.

```bash
mkdir -p ./volumes/web/cert
cp <PATH-TO-PRE-EXISTING-CERT>.pem ./volumes/web/cert/fullchain.pem
cp <PATH-TO-PRE-EXISTING-KEY>.pem ./volumes/web/cert/key.pem
```

5.Check the following lines in your `.env` file.

```bash
CERT_PATH=./volumes/web/cert/cert.pem
KEY_PATH=./volumes/web/cert/key-no-password.pem
```

6.Run Mattermost.

```bash
sudo docker compose -f docker-compose.yml -f docker-compose.nginx.yml up -d
```

7.To shut down your deployment.

```bash
sudo docker compose -f docker-compose.yml -f docker-compose.nginx.yml down
```
