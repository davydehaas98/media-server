<h1>Set some environmental variables such as timezone, user id, user group, etc. that docker containers should use.</h1>
<strong>Create / edit the environmental variables file using the following command:</strong>

sudo nano /etc/environment

<strong>Add the following as separate lines at the end of the file:</strong>

PUID=0
PGID=113
TZ="America/New_York"
USERDIR="/home/USER"
MYSQL_ROOT_PASSWORD="password"

<strong>Use this command to get the PUID (USER) and PGID (docker):</strong>
id

</strong>Use this command to get USERDIR:</strong>
cd ~ ; pwd

<strong>Log out and back in for the environmental variables to take effect.</strong>