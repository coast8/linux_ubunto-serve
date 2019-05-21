##############################
#                            #
#     PLATFORM LAMP          #
#                            #
##############################




#################################
# 1 - Instalar o Servidor Apache ############################################################################
#################################
	
	sudo apt-get update
	sudo apt-get install apache2

## sua configuração do Apache em busca de erros de sintaxe
## verificando os erros de sintaxe digitando
		sudo apache2ctl configtest

## Reinicie o Apache para implementar suas alterações:
	sudo systemctl restart apache2

## Ajustar o Firewall para Permitir Tráfego Web
	sudo ufw app list                 //certificar-se de que o UFW tem um perfil de aplicativo para o Apache
	sudo ufw app info "Apache Full"	  //ele deve mostrar que ele habilita tráfego para as portas 80 e 443:

## Permita o tráfego entrante para esse perfil:
	sudo ufw allow in "Apache Full"

## Test
	http://endereço_IP_do_seu_servidor




################################
# 2 - Instalar o Servidor MySQL	############################################################################
################################

	sudo apt-get install mysql-server

## Iniciar o MYSQL
	sudo /etc/init.d/mysql start

## Parar o MySQL
	sudo /etc/init.d/mysql stop

## Para reiniciar o MySQL
	sudo /etc/init.d/mysql restart

## Para checar o status do MySQL
	sudo /etc/init.d/mysql status

##  Installar o pacote de segurança
	sudo mysql_secure_installation




###########################
# 3 - Instalar o PHP       ############################################################################
###########################

## php i libs
	sudo apt-get install php libapache2-mod-php php-mcrypt php-mysql

## Apache olhar para um arquivo index.php primeiro.
	sudo nano /etc/apache2/mods-enabled/dir.conf
	<IfModule mod_dir.c>
	       DirectoryIndex index.php index.html index.cgi index.pl index.xhtml index.htm
	</IfModule>

##  reiniciar o servidor web Apache
	sudo systemctl restart apache2

## verificar o status do serviço apache2 
	sudo systemctl status apache2




#################################
# 4 - Instalar módulos PHP      ############################################################################
#################################

## opções disponíveis para os módulos e bibliotecas PHP
	apt-cache search php- | less

## Para obter mais informações sobre o que cada módulo faz
	apt-cache show nome_do_pacote
	apt-cache show php-cli  

## Para testar
	sudo nano /var/www/html/info.php
	http://endereço_IP_do_seu_servidor/info.php

## lib para descompactar arquivos zip
## https://stackoverflow.com/questions/45117510/ziparchive-class-is-missing-on-your-server-in-ubuntu
	sudo apt-get install php7.0-zip




#################################
# 5- Install phpMyAdmin          ############################################################################
#################################

## The easiest way to install phpmyadmin is through apt-get:
	sudo apt-get install phpmyadmin apache2-utils

## After the installation has completed, add phpmyadmin to the apache configuration.
	sudo nano /etc/apache2/apache2.conf

## Add the phpmyadmin config to the file.
	Include /etc/phpmyadmin/apache.conf

## Restart apache:
	sudo service apache2 restart

## PHPMYADMIN existem mais modulos de seguraça a serem instalados.




#################################
# 6 -  GIT-HUB                   ############################################################################
#################################
	sudo apt-get install git




# FONTES:
	https://www.digitalocean.com/community/tutorials/como-instalar-a-pilha-linux-apache-mysql-php-lamp-no-ubuntu-16-04-pt

	https://www.digitalocean.com/community/tutorials/how-to-install-and-secure-phpmyadmin-on-ubuntu-12-04
