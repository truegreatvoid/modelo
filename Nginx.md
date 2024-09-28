
# Comandos

## Complemento

### 1. Caminho do Sites-available

```bash
cd /etc/nginx/sites-available
```

### 2. Caminho do Sites-Enabled

```bash
cd /etc/nginx/sites-enabled
```

## Instalação do Nginx (Ubuntu)

### 1. Atualize o sistema
Antes de instalar qualquer novo pacote, é sempre uma boa prática garantir que todos os pacotes do sistema estejam atualizados para suas versões mais recentes.

```bash
sudo apt update
sudo apt upgrade
```

### 2. Instale o Nginx
O Nginx é um servidor web amplamente utilizado. Esse comando instala o Nginx a partir dos repositórios do Ubuntu.

```bash
sudo apt install nginx
```

### 3. Verifique o status do Nginx
Após a instalação, o Nginx normalmente inicia automaticamente. Este comando verifica se o serviço está em execução.

```bash
sudo systemctl status nginx
```

Se o serviço Nginx não estiver em execução, você pode iniciá-lo manualmente com o seguinte comando:

```bash
sudo systemctl start nginx
```

### 4. Habilite o Nginx para iniciar no boot
Isso garante que o Nginx seja iniciado automaticamente sempre que o servidor for reiniciado.

```bash
sudo systemctl enable nginx
```

### 5. Permitir o Nginx através do firewall
Se você estiver usando o `ufw` como firewall, será necessário permitir o tráfego HTTP e HTTPS para o Nginx. Este comando permite a entrada de tráfego nas portas padrão 80 (HTTP) e 443 (HTTPS).

```bash
sudo ufw app list
sudo ufw allow 'Nginx Full'
```

---

## Configuração

### 1. Criar a configuração do site
Abra o arquivo de configuração para o seu site/subdomínio. Isso definirá como o Nginx deve servir o conteúdo para o subdomínio `sos.animais.versesync.cloud`.

```bash
sudo nano /etc/nginx/sites-available/sos.animais.versesync.cloud
```

### 2. Criar um link simbólico para ativar a configuração
Depois de criar o arquivo de configuração, você precisa ativá-lo criando um link simbólico na pasta `sites-enabled`.

```bash
sudo ln -s /etc/nginx/sites-available/sos.animais.versesync.cloud /etc/nginx/sites-enabled/
```

### 3. Teste a configuração
Antes de reiniciar o Nginx, sempre é recomendado testar se as configurações estão corretas.

```bash
sudo nginx -t
```

### 4. Reinicie o Nginx
Depois de confirmar que a configuração está correta, reinicie o Nginx para aplicar as mudanças.

```bash
sudo systemctl restart nginx
```

### 5. Verifique os logs de erros
Se houver problemas, você pode monitorar o log de erros do Nginx em tempo real para verificar onde algo pode estar falhando.

```bash
sudo tail -f /var/log/nginx/error.log
```




















sudo certbot certificates


docker ps
docker stop sos-project
docker stop mongodb
docker-compose up -d










  GNU nano 7.2                          sos.animais.versesync.cloud                                   server {
    listen 443 ssl;
    server_name sos.animais.versesync.cloud;
    ssl_certificate /etc/letsencrypt/live/sos.animais.versesync.cloud/fullchain.pem; # managed by Cer>    ssl_certificate_key /etc/letsencrypt/live/sos.animais.versesync.cloud/privkey.pem; # managed by C>
    ssl_protocols TLSv1.2 TLSv1.3;
    ssl_ciphers 'ECDHE-RSA-AES128-GCM-SHA256:AES128-SHA';
    ssl_prefer_server_ciphers on;

    location / {
        root /opt/sos-project/SOS_Project/frontend/dist;
        try_files $uri /index.html;
    }

}

# Redirecionar HTTP para HTTPS
server {
    if ($host = sos.animais.versesync.cloud) {
        return 301 https://$host$request_uri;
    } # managed by Certbot


    listen 80;
    server_name sos.animais.versesync.cloud;
    return 301 https://$host$request_uri;


}


------


# Configuração para servir HTTP (sem redirecionamento)
server {
    listen 80;
    server_name sos.animais.versesync.cloud;

    # Servir o frontend diretamente via HTTP
    location / {
        root /opt/sos-project/SOS_Project/frontend/dist;
        try_files $uri /index.html;
    }
}

# Remova ou comente o bloco SSL para desativar HTTPS temporariamente
# server {
#     listen 443 ssl;
#     server_name sos.animais.versesync.cloud;

#     ssl_certificate /etc/letsencrypt/live/sos.animais.versesync.cloud/fullchain.pem; # managed by Certbot
#     ssl_certificate_key /etc/letsencrypt/live/sos.animais.versesync.cloud/privkey.pem; # managed by Certbot
#     ssl_protocols TLSv1.2 TLSv1.3;
#     ssl_ciphers 'ECDHE-RSA-AES128-GCM-SHA256:AES128-SHA';
#     ssl_prefer_server_ciphers on;

#     location / {
#         root /opt/sos-project/SOS_Project/frontend/dist;
#         try_files $uri /index.html;
#     }
# }



