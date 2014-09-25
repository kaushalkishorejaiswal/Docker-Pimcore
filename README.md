Created by Kaushal Kishore <br>
Email : kaushal.rahuljaiswal@gmail.com<br>
Website : http://www.kaushalkishore.com<br>

<h2>Dockerfile for creating docker image for Pimcore on LAMP (Linux, Apache2, MySQL, PHP)</h2>

<h4>Steps for creating image from the Docker-Pimcore:</h4>

<b>Step 1 :</b> Clone the Docker-Pimcore.git
<pre>
<b>Command: </b>
git clone https://github.com/kaushalkishorejaiswal/Docker-Pimcore.git
</pre>

<b>Step 2 :</b> Change the directory to the clone folder
<pre>
<b>Command:</b>
cd Docker-Pimcore
</pre>

<b>Step 3 :</b> Create the Docker Image
<pre>
<b>Command: </b>
sudo docker build -t ##NAME_OF_YOUR_DOCKER_IMAGE## .
</pre>

<pre>
<b>Note : </b>
  a). This command will be fired where the DockerFile will be placed
  b). ##NAME_OF_YOUR_DOCKER_IMAGE## : Replace it with your image name
  c). . : (.) Symbols shows that your Dockerfile is available on the same directory where you are running the command.
</pre>

<b>Step 4 :</b> Create an Pimcore Installed Container from the image
<b>Command Syntax: </b>
sudo docker run --name [container name] -p [port to access (New Port):port exposed(original port)] -i -t [image name]
<pre>
<b>Command:</b>
sudo docker run --name ##NAME_OF_YOUR_DOCKER_CONTAINER## -d -p 8082:80 -p3307:3306 ##NAME_OF_YOUR_DOCKER_IMAGE##
</pre>

<b>Step 5 :</b> Now you can access your Pimcore container from your web browser.
<pre>
<b>Command:</b>
http://127.0.0.1:8082/
</pre>

<b>Step 6 :</b> You can access your MySQL using the below command.
<pre>
<b>Command:</b>
mysql -uroot -proot -h172.17.42.1 -P3037
</pre>
<b>Important Notes</b>
<ul>
  <li>
    You can get the IP of the container using the command
    <ul><li>docker inspect ##Container ID##</li></ul>
  </li>
  <li>
    To get the Container ID. Use the below command
    <ul><li>docker ps -a</li></ul>
  </li>
  <li>You can also access the Apache2 using the container IP</p>
  <li>Read more details of MySQL <a href="https://github.com/kaushalkishorejaiswal/Docker-MySQL">Click Here</a></li>
</ul>

<h4>Some other important commands:</h4>
<ul>
<li><b>docker images :</b> To list all the images of your docker</li>
<li><b>docker ps :</b> To list all the runing containers</li>
<li><b>docker kill ##CONTAINER_NAME## :</b> To kill the runing container</li>
<li><b>docker rm ##CONTAINER_NAME## :</b> To delete the container from the system.</li>
<li><b>docker inspect ##CONTAINER_NAME## :</b> To get all the information about the container.</li>
<li><b>docker logs ##CONTAINER_NAME## :</b> To get the logs of the container.</li>
<li><b>docker ps -a:</b> To get the listing of all the containers.</li>
</ul>

<h4>Additional Notes:</h4>
<b>Command for attaching the volume of your hosted machine:</b>
<pre>
<b>Command Syntax:</b>
sudo docker run --name ##NAME_OF_YOUR_DOCKER_CONTAINER## -d -p 8082:80 -v ##HOSTED_VOLUME_LOCATION##:##CONTAINER_VOLUME_LOCATION## ##YOUR_IMAGE_NAME##
</pre>

<pre>
<b>Command Example:</b>
sudo docker run --name pimcore_setup -d -p 8082:80 -v /var/www/kaushal:/var/www pimcore_kaushal
</pre>

<pre>
<b>To view the Files of your container:</b>
# find ID of your running container:
docker ps

# create image (snapshot) from container filesystem
docker commit 12345678904b5 mysnapshot

# explore this filesystem using bash (for example)
docker run -t -i mysnapshot /bin/bash
</pre>
<b>Other Pimcore Important Notes:</b>
<ul>
  <li>You can change the credential of the MySQL in docker file, after setting the (MYSQL_USER,MYSQL_PASS) variables</li>
  <li>You can also change the Pimcore database name, after setting the (Pimcore_DBNAME)</li>
  <li>The hostname will be prefixed with the port during the installation of the Pimcore</li>
</ul>
<b>Related Projects</b>
<ul>
  <li>Docker-Centos-Nginx : https://github.com/kaushalkishorejaiswal/Docker-Centos-Nginx </li>
  <li>Docker-Centos-Nginx-PHP : https://github.com/kaushalkishorejaiswal/Docker-Centos-Nginx-PHP </li>
  <li>Docker-MySQL :  https://github.com/kaushalkishorejaiswal/Docker-MySQL </li>
  <li>Docker-LAMP : https://github.com/kaushalkishorejaiswal/Docker-LAMP </li>
</ul>

<b>Database Credentials:</b>
<ul>
	<li>Host : 172.17.42.1</li>
	<li>Username : root</li>
	<li>Password : root</li>
	<li>Database : pimcore</li>
</ul>
