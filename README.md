# Dockerized Plex Media Server on Linux

## Install Docker Community Edition (Docker CE) on Ubuntu
Because the Ubuntu repository does not always has the latest version that is available, you can add the latest Docker repository yourself to always be up to date.

Prepare the System to add the Docker repository:

`sudo apt-get install apt-transport-https ca-certificates curl software-properties-common`

Docker repository's GDPG key for verification of the repository:

`curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -`

Add the Docker repository:

`sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"`

Refresh the Ubuntu packages list:

`sudo apt-get update`

Install Docker Community Edition:

`sudo apt-get install docker-ce`

You can check the installed version using the following command:

`docker -version`

You can test your docker setup by using the following command:

`sudo docker run hello-world`

This command will download and run a test container.
## Install Docker Compose on Ubuntu
Install the latest verstion of Docker Compose that is available using the curl command on GitHub [here](https://github.com/docker/compose/releases).

You can check the installed version using the following command:

`docker-compose --version`

## Add Linux User to Docker Group
Running and managing docker containers requires sudo privileges. You can give docker these priviliges by using the following command:
    
`sudo usermod -aG docker ${USER}`

## Setup Environmental Variables for Docker
Next, you have to set some environmental variables that Docker containers should use.
Create and edit the environmental variables file using the following command:

`sudo nano /etc/environment`

Add the following as separate lines at the end of the file:

```
PUID=0
PGID=113
TZ="America/New_York"
USERDIR="/home/USER"
MYSQL_ROOT_PASSWORD="password"
```

`PUID` and `PGID` are the user ID of the linux user, who you want to run the home server apps as, and group ID of docker. These can be obtained using the `id` command. Look for the uid= and the groups=(docker) variables and fill them in your /etc/environment file.

`TZ` is the timezone that you want to set for your containers. Get your TZ from this [Timezone Database](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones).

`USERDIR` is the path to the home folder of the current user. You can get this by using the following command:
    
`cd ~ ; pwd`

`MYSQL_ROOT_PASSWORD` is used for the MariaDB and phpMyAdmin MYSQL administrator password.

**You will need to logout and log back in for the environmental variables to take effect.**
