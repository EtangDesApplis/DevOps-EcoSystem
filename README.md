
# Install docker
```
sudo apt install apt-transport-https ca-certificates curl software-properties-common gnupg
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo apt-key fingerprint 0EBFCD88
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
sudo apt update
sudo apt install docker-ce
sudo usermod -aG docker $USER
sudo reboot
```

# Install docker compose
```
sudo curl -L "https://github.com/docker/compose/releases/download/1.26.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
```
# Set up
```
mkdir -p data-artifactory && \
chmod -R 777 data-artifactory && \
mkdir -p data-gitlab/config && \
mkdir -p data-gitlab/data && \
mkdir -p data-gitlab/logs && \
mkdir -p data-sonarqube/conf && \
mkdir -p data-sonarqube/data && \
mkdir -p data-sonarqube/extensions && \
mkdir -p data-sonarqube/logs && \
mkdir -p data-jenkins

```

# Start eco-system
```
docker-compose up -d
```
Gitlab is avaiable at: [a link](http://localhost:80)
default user is root (password reset will be asked for the first time of connection)
ssh is available through port 2222 (we reserve 22 for Jenkins slave by ssh)

Jenkins is available at: [a link](http://localhost:8080)

Artifactory is available at: [a link](http://localhost:8082/ui/)
The authenticaion by default is: admin/password

Sonar is available at : [a link](http://localhost:9000)
The authenticaion by default is: admin/admin

# Stop eco-system
```
docker-compose down
```

# Uninstall docker, docker compose
```
sudo rm /usr/local/bin/docker-compose
sudo apt remove docker docker-engine docker.io
```

