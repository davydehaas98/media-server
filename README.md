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

## Create Linux User for Docker usage
You need to create a seperate user and add it to the `docker` group, because some containers will not run secure and properly when using the root user.
You can create a new non-root user by using the command seen below. Change `<name>` to whatever you want. I personally named the user that will own everything related to Docker just `docker`.

`useradd -r -g docker <name>`

These commands will make sure your user can properly access the mediaserver files:

`chown -R <name>:docker /home/<name>`

`chmod -R 0755 /home/<name>`

## Add Linux User to Docker Group
Running and managing Docker containers requires sudo privileges. You can give the user these priviliges by using the following command:

`sudo usermod -aG docker ${USER}`

## Setup Environmental Variables for Docker
Next, you have to set some environmental variables that Docker containers should use.
These environmental variables will be used in the docker-compose.yml file by using `${X}` where `X` is the name of the variable.

Create and edit the environmental variables file using the following command:

`sudo nano /etc/environment`

Add the following as separate lines at the end of the file:

```
PUID=999
PGID=113
TZ="America/New_York"
USERDIR="/home/<name>"
OPENVPN_USERNAME="username"
OPENVPN_PASSWORD="password"
TORRENT_USERNAME="username"
TORRENT_PASSWORD="password"
```

`PUID` and `PGID` are the user ID of the linux user, who you want to run the home server apps as, and group ID of docker. These can be obtained using the `id` command. Look for the uid=(<name>) and the groups=(docker) variables and fill them in your /etc/environment file.

`TZ` is the timezone that you want to set for your containers. Get your TZ from this [Timezone Database](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones).

`USERDIR` is the path to the home folder of the non-root user. Change `<name>` to the name of the user you created that will run docker

`OPENVPN_USERNAME` and `OPENVPN_PASSWORD` is used for logging into your VPN account.

`TORRENT_USERNAME` and `TORRENT_PASSWORD` is used for setting up your torrent client with a secure login.

**You will need to logout and log back in for the environmental variables to take effect. If that does not work you have to reboot.**
