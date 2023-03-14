# dockerize

# first: 
# After cloning this project, ensure that you move these files into your Laravel application.  

.docker  
docker-compose.yml  

# Ensure that you set different ports for each project. 
# Example:

APP_URL=http://127.0.0.1:9011  
APP_PORT=9011  

CRONJOB_PORT=9012  

PHPMYADMIN_PORT=9013  
FILEBROWSER_PORT=9014  
REDIS_PORT=9015  
DB_PORT=9016  

DB_HOST=host.docker.internal  

To dockerize the project cmd:  
docker-compose up --build -d 

Note! Please ensure that you have installed and set up Docker before proceeding.
