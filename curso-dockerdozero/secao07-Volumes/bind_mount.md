Bind Mount - persistindo dados em pastas
============

$ nano index.html: "<h1>Teste</h1>"
$ docker run -itd --name apache -p 8080:80 -v /docker/site:/usr/local/apache2/htdocs/ httpd:2.4
$ docker inspect apache | grep Mounts

* 01 - Verificar data do container anterior:
$>  sudo docker exec -it apache date

* 02 - Remover container e criar, novamente, compartilhando timezone do host:
$>  sudo docker rm -f apache

* Read-only
$>  sudo docker run -itd --name apache -p 8080:80 -v /etc/localtime:/etc/localtime:ro -v /docker/site:/usr/local/apache2/htdocs/ httpd:2.4

