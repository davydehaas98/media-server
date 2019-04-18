Set some environmental variables such as timezone, user id, user group, etc. that docker containers should use.
Create / edit the environmental variables file using the following command:

sudo nano /etc/environment

Add the following as separate lines at the end of the file:

PUID=0
PGID=113
TZ="America/New_York"
USERDIR="/home/USER"
MYSQL_ROOT_PASSWORD="password"

Use this command to get the PUID (USER) and PGID (docker):
id

Use this command to get USERDIR:
cd ~ ; pwd

Log out and back in for the environmental variables to take effect.