# dockerize

# first: 
# after cloning this project make sure to move these file inside your laravel app 

.docker  
docker-compose.yml  

# then make sure to set different ports for each project
# Example:

APP_URL=http://127.0.0.1:9011  
APP_PORT=9011  

CRONJOB_PORT=9012  

PHPMYADMIN_PORT=9013  
FILEBROWSER_PORT=9014  
REDIS_PORT=9015  
DB_PORT=9016  

DB_HOST=host.docker.internal  
