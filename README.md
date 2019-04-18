<h1>Set some environmental variables such as timezone, user id, user group, etc. that docker containers should use.</h1>
<h2>Create / edit the environmental variables file using the following command:</h2>

sudo nano /etc/environment

<h2>Add the following as separate lines at the end of the file:</h2>

PUID=0
PGID=113
TZ="America/New_York"
USERDIR="/home/USER"
MYSQL_ROOT_PASSWORD="password"

<h2>Use this command to get the PUID (USER) and PGID (docker):</h2>
id

</h2>Use this command to get USERDIR:</h2>
cd ~ ; pwd

<h2>Log out and back in for the environmental variables to take effect.</h2>