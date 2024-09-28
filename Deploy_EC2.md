COnfiguracao de DNS

Feito a compra do dominio por ANY host
Hostinger -> DNS/Nameservers

ALterar o nameservers da Hostinger e colocar o da CLoudFlare 

O provedor que irá gerenciar o  dns será a Cloud Flare..

Na CLoudFlare 

DNS -> Records 

configurar seu dns

type sendo A
name adicionar seu @ (dominio) e sub dominios apontando para o ipv4 publico da sua ec2

saida:

A api.sos.animais 18.229.138.196
A sos.animais 18.229.138.196
A versesync.cloud 18.229.138.196

dps de ter feito isso ir em SSL/TLS e configurar o Mode encryption como Full (strict)

Enable encryption end-to-end and enforce validation on origin certificates. Use Cloudflare’s Origin CA to generate certificates for your origin.

**entra aqui o texto explicando os tipos de modo**

Vai em configure e selecione o modo correto -> Full (strict)

dos va em SSL/TLS 

Origin Server 

crie seu Certificado 

usando a configuracao Generate private key and CSR with Cloudflare
Private key type
RSA (2048)
List the hostnames 

coloque seu dominio e sub dominio e o dominio com pre-fixo *

**explicacao do porque**

selecione 
