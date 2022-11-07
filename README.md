Para a Instalação do Sonar com o arquivo docker-compose é necessario a instalação do Docker

### Instalação do Docker e Docker compose Ubuntu:

sudo apt install docker docker-compose

### Instalação do Docker e Docker compose no centos:

Docker
yum-config-manager  https://download.docker.com/linux/centos/docker-ce.repo 
yum install docker-ce

Docker Compose
curl -L "https://github.com/docker/compose/releases/download/2.12.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

Atribuindo permissão de execução para o binario do docker-compose
chmod +x /usr/local/bin/docker-compose

Criando Link Simbolico para que não haja nenhum problema para execução do docker-compose.
ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose

## Configurar Limits no Sistema Operacional | Obs: Validos somente para linux
1 - Um dos pré requisitos para instalação é ajuste em alguns limits do linux, sendo eles:

vm.max_map_count is greater than or equal to 524288
fs.file-max is greater than or equal to 131072
the user running SonarQube can open at least 131072 file descriptors
the user running SonarQube can open at least 8192 threads

para atualizar os dois primeiros valores é necessario editar o arquivo /etc/sysctl.conf e inserir as seguintes linhas:

vm.max_map_count= 524288
fs.file-max= 131072

para atualizar os dois ultimos é necessario editar o arquivo /etc/security/limits.conf e inserir as linhas abaixo:

root             -       nofile          131072
root             -       nproc           8192


## Instalação do sonarqube

Para iniciar o container do sonar e do postgre , basta executar o comando $ docker-compose up -d , lembrando que você precisa está no diretorio onde está localizado o docker-compose.yml.

Após isso basta acessar a URL http://$(seuip):(porta)
