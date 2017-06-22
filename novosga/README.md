# Novo SGA

Sistema de gerenciamento de atendimento: [http://novosga.org](http://novosga.org)


## docker-compose.yml

```yml
novosga:
  image: novosga/novosga:1.5.1
  ports:
    - "80:80"
  links:
    - mysql
  restart: always

mysql:
  image: mysql:latest
  environment:
    - MYSQL_ROOT_PASSWORD=root
    - MYSQL_DATABASE=novosga
    - MYSQL_USER=novosga
    - MYSQL_PASSWORD=novosga
  restart: always

```
