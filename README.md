<h1>Media Server for Personal Use</h1>
<h2>Set some environmental variables such as timezone, user id, user group, etc. that all the docker containers in the media-server should use.</h2>
<h3>Create and edit the environmental variables file using the following command:</h3>
<p>sudo nano /etc/environment</p>

<h3>Add the following as separate lines at the end of the file:</h3>
<p>PUID=0</p>
<p>PGID=113</p>
<p>TZ="America/New_York"</p>
<p>USERDIR="/home/USER"</p>
<p>MYSQL_ROOT_PASSWORD="password"</p>

<h3>Use this command to get the PUID (USER) and PGID (docker):</h3>
<p>id</p>

<h3>Use this command to get USERDIR:</h3>
<p>cd ~ ; pwd</p>

<strong>Log out and back in for the environmental variables to take effect.</strong>
