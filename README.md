# dockerphp

#use docker file to build apache/php image 
docker build -t php-server.

#start mysql container with data stored in container 
docker run --name mysql -e MYSQL_ROOT_PASSWORD=password -d mysql

#start mysql container with data stored on host 
docker run -v /home/mysql-data:/var/lib/mysql --name mysql -e MYSQL_ROOT_PASSWORD=password -d mysql

#start webserver links to mysql conatiner 
docker run -p 8080:80 --name phpapp --link mysql:mysql  -d php-server


#future need to script the configuration on the mysql db

