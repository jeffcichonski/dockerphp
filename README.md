# dockerphp

#use docker file to build apache/php image 
docker build -t phpsite .

#start mysql container 
docker run --name mysql -e MYSQL_ROOT_PASSWORD=password -d mysql

#start webserver with php container 
docker run -p 8080:80 -d phpsite

#links to mysql
docker run -p 8080:80 --name phpapp --link mysql:mysql  -d phpsite

#will need to change db info in index.php test page for this test env manually create the db it is trying to insert into
#future need to script the configuration on the mysql db
#need to store db outsite of the conatiner and connect to that drive when container starts 
