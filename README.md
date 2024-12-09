# Deployment-Setup
sudo apt install nginx
sudo nano /etc/nginx/conf.d/server.conf
Add the following to the location part of the server block
server {
  listen 80;
  server_name <here add your domain name>; 

  location / {
      proxy_pass http://127.0.0.1:8000; # here your port number 
      proxy_set_header Host $host;
      proxy_set_header X-Real-IP $remote_addr;
      proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
      proxy_set_header X-Forwarded-Proto $scheme;
  }
}

Check nginx config
sudo nginx -t

restart nginx

sudo systemctl restart nginx
