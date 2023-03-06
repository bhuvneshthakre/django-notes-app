# Simple Notes App
This is a simple notes app built with React and Django.

## Requirements
1. Python 3.9
2. Node.js
3. React

## Installation
1. run an ubuntu ec2 instance with http & htpps security group in it and floow the commands
```
sudo apt-get update
sudo apt-get install nginx  >> Install Nginx reverse proxy to make this application available
systemctl enable nginx   >> it will start nginx & check status 
sudo apt-get docker.io
sudo usermod -aG docker $USER    >> it give permission to run docker
```

2. Clone the repository
```
git clone https://github.com/LondheShubham153/django-notes-app.git
```

3. Build the app
```
docker build -t notes-app .
```

4. Run the app
```
docker run -d -p 8000:8000 notes-app:latest
docker ps   >> will show the container is running
sudo reboot  >> it will reboot the system
```
5. see where the container is running
```
curl -L http://127.0.0.1:8000 >> it is running locally on public ip
```
6. here comes important part
```
cd /etc/nginx/sites-enabled/  >> its a root folder in your system
nano default  >> default is the file in root folder we have to edit it
proxy_pass http://127.0.0.1:8000;   >> pass it in location/
sudo systemctl restart nginx
refresh the public ip it will show react in it with blank page
```
7. copying the frontend & backend file in the root folder
```
sudo cp -r * /var/www/html/   > from mynotes>bulid copy the frontend & from api copy the backend and reboot the system 
and finally the app is up and running
 



