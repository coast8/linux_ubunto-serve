

#####################
## wget             ##-----------------------------------------------------------------
#####################

# baixando o atualizado wget
	wget http://curl.haxx.se/download/curl-7.50.3.tar.gz
	tar -xvf curl-7.50.3.tar.gz
	cd curl-7.50.3/
	./configure
	make
	sudo make install

#  vendo a versao
	curl --version



#####################
## COMANDOS cron   ##-----------------------------------------------------------------
#####################

# Este comando lista as tarefas cron.
	crontab -l
# Este comando editar as tarefas cron.
	crontab -e



#################
## Referencias ##-----------------------------------------------------------------
#################

# Boson Treinamementos - Comando cron - Agendar tarefas para execução recorrente no Linux
	https://www.youtube.com/watch?v=GGTbXq1FUI0

# O que é cron
	https://www.infowester.com/linuxcron.php

# cron-command-to-run-url-address-every-5-minutes
	https://stackoverflow.com/questions/11375260/cron-command-to-run-url-address-every-5-minutes

# o que é o curl
	https://pt.stackoverflow.com/questions/58752/o-que-%C3%A9-curl-curl-setopt

# 	/dev/null
	https://www.poftut.com/linux-dev-null-explanation/