# 42 FT_SERVER

## PREREQUISITE

Before all, be sure that DOCKER is set and works on your system.
[docs.docker.com/get-docker/](https://docs.docker.com/get-docker/)

If you evaluate this FT_SERVER project on the VM42 engine, run
`systemctl stop nginx`
to stop default nginx process.

## LAUNCH

At the root of the repository

Build the docker_image from the docker file
`docker build -t ft_server .`

Launch the container
`docker run -ti -p 443:443 -p 80:80 ft_server`

On your browser , go on 
[https://localhost/](https://localhost/)
to test.

## TESTING

To connect to PhpMyAdmin
```
user: admin
password: 1234
```

### NEW HTML PAGE
Go on 
[https://localhost/wordpress/test.html](https://localhost/wordpress/test.html)
There 's nothing.
Now go on 
`cd tests`
and run
```
./test_html.sh
```
and refresh the page.

### DATABASE
To test db launch 
`cd ./tests`
and
```
./test_db.sh
```
This will create a new table inside the current database.
A new web page will be created to show this new datas
[https://localhost/wordpress/42_projects.php](https://localhost/wordpress/42_projects.php)
And this new table will of course appear inside phpmyadmin dashboard.

### AUTOINDEX
To test autoindex, at the root of the container
```
./autoindex.sh
```
and refresh your page on your browser.
When autoindex is OFF you will redirect on the wordpress page.
You can relaunch this command to switch the autoindex and observe the behaviour of your localhost.
[https://localhost/](https://localhost/)

### SSL
Check the httpS inside the url

## QUIT

to quit the container 
`CTRL + D`

## CLEAN IMAGES

To delete docker images you've built during the evaluation launch
`docker image rm -f ft_server debian:buster`





