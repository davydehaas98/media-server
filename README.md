<h1>Set some environmental variables such as timezone, user id, user group, etc. that docker containers should use.</h1>
<strong>Create/edit the environmental variables file using the following command:</strong>

<p>sudo nano /etc/environment</p>

<strong>Add the following as separate lines at the end of the file:</strong>

<p>PUID=0</p>
<p>PGID=113</p>
<p>TZ="America/New_York"</p>
<p>USERDIR="/home/USER"</p>
<p>MYSQL_ROOT_PASSWORD="password"</p>

<strong>Use this command to get the PUID (USER) and PGID (docker):</strong>

<p>id</p>

<strong>Use this command to get USERDIR:</strong>

<p>cd ~ ; pwd</p>

<strong>Log out and back in for the environmental variables to take effect.</strong>