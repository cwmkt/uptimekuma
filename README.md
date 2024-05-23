<p align="center">
<img src="https://cwmkt.com.br/wp-content/uploads/2024/04/logo_github.png" width="240" />
<p align="center">Seja bem-vindo ao Guia de Instalação do Uptime Kuma 🚀</p>
</p>
  
<p align="center"> 
<a href="https://hubconnect.top" target="_blank">👉 Participe da Comunidade HubConnect 👈</a>
</p>

<hr />
<hr />

 
### Manual de Instalação Uptime Kuma

Atualize os pacotes da sua máquina

```bash
sudo apt update && apt upgrade -y
```

```bash
apt install docker-compose
```

```bash
docker run -d --restart=always -p 3001:3001 -v uptime-kuma:/app/data --name uptime-kuma louislam/uptime-kuma:1
```

### Instalação do Nginx proxy reverso

```bash
sudo apt install nginx
```

```bash
sudo nano /etc/nginx/sites-available/uptimekuma
```

```bash
server {
  server_name uptimekuma.dominio.com.br;
  
  underscores_in_headers on;

  location / {

   proxy_pass http://127.0.0.1:3001;
   proxy_pass_header Authorization;
   proxy_set_header Upgrade $http_upgrade;
   proxy_set_header Connection "upgrade";
   proxy_set_header Host $host;
   proxy_set_header X-Forwarded-Proto $scheme;
   proxy_set_header X-Forwarded-Ssl on; # Optional
   proxy_set_header X-Real-IP $remote_addr;
   proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
   proxy_http_version 1.1;
   proxy_set_header Connection "";
   proxy_buffering off;
   client_max_body_size 0;
   proxy_read_timeout 36000s;
   proxy_redirect off;
  }
  add_header Strict-Transport-Security "max-age=31536000; includeSubDomains" always;
  ssl_protocols TLSv1.2 TLSv1.3;
} 
  ```

```bash
sudo ln -s /etc/nginx/sites-available/uptimekuma /etc/nginx/sites-enabled
```

```bash
sudo apt-get install snapd
```

```bash 
sudo snap install notes
```

```bash
sudo snap install --classic certbot
```

```bash  
sudo certbot --nginx
```

```bash  
sudo service nginx restart
```

### Pronto ✅ Instalação concluída
