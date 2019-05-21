##############################
#                            #
#             Users          #
#                            #
##############################

# Tutorial 1

## Quando você instala o Ubuntu, normalmente o primeiro acesso será a partir do usuário root. Embora isso lhe dá o poder de fazer todas as alterações necessárias no servidor, recomendamos criar um novo usuário com privilégios de root no servidor. Além disso, se outras pessoas estarão acessando o servidor, você precisará criar novos usuários para eles também. Neste tutorial abordaremos de forma superficial sobre como criar um novo usuário, concedendo-lhes privilégios de root, e exclusão de usuários.

## Quando você executa todas as tarefas root com o novo usuário, você terá que usar a frase “sudo” antes do comando. Este é um comando útil por 2 motivos: 1)  impede o usuário de fazer qualquer sistema de destruição erros 2) armazena todos os comandos executados com sudo em um arquivo onde poderão ser revistos mais tarde, se necessário. Tenha em mente, contudo, que este usuário é tão poderoso como o usuário root.


#### add new user 
	sudo adduser novo_usuario

#### file users sudoers
	sudo /usr/sbin/visudo

#### Adicionando o nome do usuário e as mesmas permissões como root sob a especificação de privilégios do usuário irá conceder-lhes os privilégios sudo.
	# User privilege specification
	root            ALL=(ALL:ALL) ALL 
	novo_usuario    ALL=(ALL:ALL) ALL

#### delete user
	sudo userdel novo_usuario

#### delete folder home user
	sudo rm -rf /home/novo_usuario


# Fonte:
	http://wime.com.br/2013/06/06/como-adicionar-e-excluir-usuarios-no-ubuntu-12-04-e-centos-6/








/************************************ // **************************************************//








# Tutorial 2

# criando um usuario do grupo root/sudo
	adduser sammy					
	usermod -aG sudo sammy
	su - sammy
	exit


# Fonte:
	https://www.digitalocean.com/community/tutorials/configuracao-inicial-de-servidor-com-ubuntu-16-04-pt








/************************************ // **************************************************//

# Comandos relativos aos Usuarios 

## ver todos os usarios do sistema com detalhes
	getent passwd

## somente o nome dos usuarios
	getent passwd | cut -d \: -f1
