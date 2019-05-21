############################
#                          #   
# instalar Tomcat versao 8 #
#                          #
############################




## These operations were tested on UBUNTU 16




############################################
# 1 - Instalando JDK
############################################
	sudo apt-get update

## Java Development Kit (JDK)
	sudo apt-get install default-jdk

## Once Java is installed, you can verify the installed Java version using the following command:
	java -version




############################################
# 2 - Create Tomcat User
############################################
	sudo groupadd tomcat
	sudo useradd -s /bin/false -g tomcat -d /opt/tomcat tomcat




############################################
# 3 - Installing Tomcat
#############################################
	wget http://apache.mirrors.ionfish.org/tomcat/tomcat-8/v8.5.5/bin/apache-tomcat-8.5.5.tar.gz

	sudo tar -xzvf apache-tomcat-8.5.5.tar.gz

	sudo mv apache-tomcat-8.5.5 /opt/tomcat

## Next you will need to give proper permission to the tomcat user to access to 
## the Tomcat installation.
	sudo chgrp -R tomcat /opt/tomcat
	sudo chown -R tomcat /opt/tomcat
	sudo chmod -R 755 /opt/tomcat




############################################
# 4 - Create a systemd Service File
############################################

## Create the systemd service file, tomcat.service, 
## inside the /etc/systemd/system/ directory.
	sudo nano /etc/systemd/system/tomcat.service

	[Unit]
	Description=Apache Tomcat Web Server
	After=network.target

	[Service]
	Type=forking

	Environment=JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64/jre
	Environment=CATALINA_PID=/opt/tomcat/temp/tomcat.pid
	Environment=CATALINA_HOME=/opt/tomcat
	Environment=CATALINA_BASE=/opt/tomcat
	Environment='CATALINA_OPTS=-Xms512M -Xmx1024M -server -XX:+UseParallelGC'
	Environment='JAVA_OPTS=-Djava.awt.headless=true -Djava.security.egd=file:/dev/./urandom'

	ExecStart=/opt/tomcat/bin/startup.sh
	ExecStop=/opt/tomcat/bin/shutdown.sh

	User=tomcat
	Group=tomcat
	UMask=0007
	RestartSec=15
	Restart=always

	[Install]
	WantedBy=multi-user.target


## Save the file and reload the systemd daemon with the following command:
	sudo systemctl daemon-reload

## Now start the Tomcat service and check the status:
	sudo systemctl start tomcat
	sudo systemctl status tomcat

## Configure the Tomcat service to start during boot:
	sudo systemctl enable tomcat

## Allow Tomcat Through the Firewall
	sudo ufw allow 8080

## Testing Tomcat
	 http://your-server-ip:8080 




# FONTE:
	https://devops.profitbricks.com/tutorials/how-to-install-and-configure-tomcat-8-on-ubuntu-1604/
	https://www.digitalocean.com/community/tutorials/how-to-install-apache-tomcat-8-on-ubuntu-16-04