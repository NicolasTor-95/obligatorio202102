################ Despligue de aplicaciones a traves de Ansible para RedHad / Debian ################

En este documento se explicara como utilizar / modificar los Script de despliegue de aplicaciones para servidores
de familia RedHad o Debian .


################ Requisitos de despliegue ################

* Instalar un primer servidor que será utilizado de Bastión o controlador.
* Generar en el mismo claves publicas/privadas (keygen-gen) para desplegar en los servidores a aplicar los Playbooks.
* Se debe de crear un usuario "Ansible" (perteneciente al grupo "sudoers") en el Controlador 
y resto de los servidores (de igual password) .
* Instalar en el controlador :
	*GIT
	*Ansible 

* Clonacion del repositorio en cuestion. https://github.com/NicolasTor-95/ansible_taller2021-1	
* En el repositorio clonado, adaptar el inventario (archivo "Host") a su ambiente, incluyendo Hostname e IP Adress.
	Encontrará ejemplos de servidores en el documento para tomar de referencia .

################  ¿Qué encontrará ya configurado? ################ 

Playbook de despligue de aplicaciones Web y de Base de Datos.
	Aplicaciones web:
		Aplicaciones Debian: 
			- iptables
			- apache2
			- php
			- php-mysql
			- git
			- python3-semanage
			- python3-selinux
			- selinux-basics
			- selinux-utils
			- policycoreutils

		Aplicaciones RedHad:
			- iptables-services
			- httpd
			- php
			- php-mysql
			- git
			- python3-libsemanage
			- python3-libselinux	
			
	Aplicaciones de Base de Datos:
		Aplicaciones RedHad:
			- mariadb-server
			- python3-PyMySQL
			- python3-libselinux
			- python3-libsemanage
			- iptables-services

		Aplicaciones Debian: 
			- mariadb-server
			- python3-PyMySQL
			- python3-selinux
			- python3-semanage
			- iptables
			- selinux-utils
			- selinux-basics
			- policycoreutils
			
			
*********** Para todos los casos se iniciaran los servicios, haran reinicios necesario, etc. ***********

################  ¿Como personalizar los paquetes a desplegar? ################ 

Dirigirse a:
/lamp_simple/group_vars/dbservers 		   	-> Paquetes para servidores de Base de Datos *
/lamp_simple/group_vars/webservers   		-> Paquetes para servidores Web *


*Adicionar a la lista que corresponda los aplicativos deseados.


Configuraciones especificas para cada grupo o en general:

/lamp_simple/roles/db/tasks/main.yml 			 -> Configurar los Task de Base de Datos para los nuevos paquetes .

/lamp_simple/roles/web/tasks/install_httpd.yml	 -> Configurar los Task de aplicaciones web para los nuevos paquetes .

/lamp_simple/roles/common/tasks/main.yml	     -> Aqui encontrara configuraciones generales para ambos casos, como puede ser Servidor NTP, SELinux Activo.

################  Ejecución del Playbook ################ 

Dirigirse a :
	/lamp_simple/

Ejecutar :
	ansible-playbook site.yml --ask-become-pass
	
Introducir la password seteada para el usuario Ansible.

Resultado:
	¡Servidores web y de base de datos RedHad y Debian configurados automaticamente!
	
	
	
Consideraciones a tener en cuenta:
	*	Siempre tener las reglas de Firewall o segmentaciones de redes configuradas correctamente, de manera tal que el Controlador
		pueda acceder al resto de los equipos.
	*	Nunca configurar Ansile con ROOT , esto es una brecha de seguridad grande .
	
	
	
	
################ Deployment of applications through Ansible for RedHad / Debian ################

This document will explain how to use / modify the application deployment scripts for servers
RedHad or Debian family.


################ Deployment requirements #################

* Install a first server that will be used as Bastion or controller.
* Generate in the same public / private keys (keygen-gen) to deploy on the servers to apply the Playbooks.
* A user "Ansible" (belonging to the group "sudoers") must be created in the Controller
and the rest of the servers (with the same password).
* Install on controller:
	* GIT
	* Ansible

* Cloning of the repository in question. https://github.com/NicolasTor-95/ansible_taller2021-1
* In the cloned repository, adapt the inventory ("Host" file) to your environment, including Hostname and IP Address.
You will find examples of servers in the document for reference.

################ What will you find already configured? ################

Playbook for the deployment of Web and Database applications.
	Web applications:
		Debian applications:
			- iptables
			- apache2
			- php
			- php-mysql
			- git
			- python3-semanage
			- python3-selinux
			- selinux-basics
			- selinux-utils
			- policycoreutils

		RedHad applications:
			- iptables-services
			- httpd
			- php
			- php-mysql
			- git
			- python3-libsemanage
			- python3-libselinux

	Database Applications:
		RedHad applications:
			- mariadb-server
			- python3-PyMySQL
			- python3-libselinux
			- python3-libsemanage
			- iptables-services

	Debian applications:
			- mariadb-server
			- python3-PyMySQL
			- python3-selinux
			- python3-semanage
			- iptables
			- selinux-utils
			- selinux-basics
			- policycoreutils

*********** In all cases the services will be started, necessary restarts, etc. ***********

################ How to customize the packages to be deployed? ################

Go to:
/ lamp_simple / group_vars / dbservers -> Packages for Database servers *
/ lamp_simple / group_vars / webservers -> Packages for web servers *


* Add the desired applications to the corresponding list.


Specific settings for each group or in general:

/lamp_simple/roles/db/tasks/main.yml -> Configure Database Tasks for new packages.

/lamp_simple/roles/web/tasks/install_httpd.yml -> Configure the web application tasks for the new packages.

/lamp_simple/roles/common/tasks/main.yml -> Here you will find general settings for both cases, such as NTP Server, SELinux Active.

################ Execution of the Playbook #################

Go to :
/ lamp_simple /

Run :
ansible-playbook site.yml --ask-become-pass

Enter the password set for the Ansible user.

Result:
RedHad and Debian web and database servers configured automatically!



Considerations to take into account:
	* Always have the Firewall rules or network segmentations correctly configured, so that the Controller
can access the rest of the equipment.
	* Never configure Ansile with ROOT, this is a big security gap.




################ Despligue de aplicaciones a traves de Ansible para RedHad / Debian ################

En este documento se explicara como utilizar / modificar los Script de despliegue de aplicaciones para servidores
de familia RedHad o Debian .


################ Requisitos de despliegue ################

* Instalar un primer servidor que será utilizado de Bastión o controlador.
* Generar en el mismo claves publicas/privadas (keygen-gen) para desplegar en los servidores a aplicar los Playbooks.
* Se debe de crear un usuario "Ansible" (perteneciente al grupo "sudoers") en el Controlador 
y resto de los servidores (de igual password) .
* Instalar en el controlador :
	*GIT
	*Ansible 

* Clonacion del repositorio en cuestion. https://github.com/NicolasTor-95/ansible_taller2021-1	
* En el repositorio clonado, adaptar el inventario (archivo "Host") a su ambiente, incluyendo Hostname e IP Adress.
	Encontrará ejemplos de servidores en el documento para tomar de referencia .

################  ¿Qué encontrará ya configurado? ################ 

Playbook de despligue de aplicaciones Web y de Base de Datos.
	Aplicaciones web:
		Aplicaciones Debian: 
			- iptables
			- apache2
			- php
			- php-mysql
			- git
			- python3-semanage
			- python3-selinux
			- selinux-basics
			- selinux-utils
			- policycoreutils

		Aplicaciones RedHad:
			- iptables-services
			- httpd
			- php
			- php-mysql
			- git
			- python3-libsemanage
			- python3-libselinux	
			
	Aplicaciones de Base de Datos:
		Aplicaciones RedHad:
			- mariadb-server
			- python3-PyMySQL
			- python3-libselinux
			- python3-libsemanage
			- iptables-services

		Aplicaciones Debian: 
			- mariadb-server
			- python3-PyMySQL
			- python3-selinux
			- python3-semanage
			- iptables
			- selinux-utils
			- selinux-basics
			- policycoreutils
			
			
*********** Para todos los casos se iniciaran los servicios, haran reinicios necesario, etc. ***********

################  ¿Como personalizar los paquetes a desplegar? ################ 

Dirigirse a:
/lamp_simple/group_vars/dbservers 		   	-> Paquetes para servidores de Base de Datos *
/lamp_simple/group_vars/webservers   		-> Paquetes para servidores Web *


*Adicionar a la lista que corresponda los aplicativos deseados.


Configuraciones especificas para cada grupo o en general:

/lamp_simple/roles/db/tasks/main.yml 			 -> Configurar los Task de Base de Datos para los nuevos paquetes .

/lamp_simple/roles/web/tasks/install_httpd.yml	 -> Configurar los Task de aplicaciones web para los nuevos paquetes .

/lamp_simple/roles/common/tasks/main.yml	     -> Aqui encontrara configuraciones generales para ambos casos, como puede ser Servidor NTP, SELinux Activo.

################  Ejecución del Playbook ################ 

Dirigirse a :
	/lamp_simple/

Ejecutar :
	ansible-playbook site.yml --ask-become-pass
	
Introducir la password seteada para el usuario Ansible.

Resultado:
	¡Servidores web y de base de datos RedHad y Debian configurados automaticamente!
	
	
	
Consideraciones a tener en cuenta:
	*	Siempre tener las reglas de Firewall o segmentaciones de redes configuradas correctamente, de manera tal que el Controlador
		pueda acceder al resto de los equipos.
	*	Nunca configurar Ansile con ROOT , esto es una brecha de seguridad grande .
	
	
	
	
################ Deployment of applications through Ansible for RedHad / Debian ################

This document will explain how to use / modify the application deployment scripts for servers
RedHad or Debian family.


################ Deployment requirements #################

* Install a first server that will be used as Bastion or controller.
* Generate in the same public / private keys (keygen-gen) to deploy on the servers to apply the Playbooks.
* A user "Ansible" (belonging to the group "sudoers") must be created in the Controller
and the rest of the servers (with the same password).
* Install on controller:
	* GIT
	* Ansible

* Cloning of the repository in question. https://github.com/NicolasTor-95/ansible_taller2021-1
* In the cloned repository, adapt the inventory ("Host" file) to your environment, including Hostname and IP Address.
You will find examples of servers in the document for reference.

################ What will you find already configured? ################

Playbook for the deployment of Web and Database applications.
	Web applications:
		Debian applications:
			- iptables
			- apache2
			- php
			- php-mysql
			- git
			- python3-semanage
			- python3-selinux
			- selinux-basics
			- selinux-utils
			- policycoreutils

		RedHad applications:
			- iptables-services
			- httpd
			- php
			- php-mysql
			- git
			- python3-libsemanage
			- python3-libselinux

	Database Applications:
		RedHad applications:
			- mariadb-server
			- python3-PyMySQL
			- python3-libselinux
			- python3-libsemanage
			- iptables-services

	Debian applications:
			- mariadb-server
			- python3-PyMySQL
			- python3-selinux
			- python3-semanage
			- iptables
			- selinux-utils
			- selinux-basics
			- policycoreutils

*********** In all cases the services will be started, necessary restarts, etc. ***********

################ How to customize the packages to be deployed? ################

Go to:
/ lamp_simple / group_vars / dbservers -> Packages for Database servers *
/ lamp_simple / group_vars / webservers -> Packages for web servers *


* Add the desired applications to the corresponding list.


Specific settings for each group or in general:

/lamp_simple/roles/db/tasks/main.yml -> Configure Database Tasks for new packages.

/lamp_simple/roles/web/tasks/install_httpd.yml -> Configure the web application tasks for the new packages.

/lamp_simple/roles/common/tasks/main.yml -> Here you will find general settings for both cases, such as NTP Server, SELinux Active.

################ Execution of the Playbook #################

Go to :
/ lamp_simple /

Run :
ansible-playbook site.yml --ask-become-pass

Enter the password set for the Ansible user.

Result:
RedHad and Debian web and database servers configured automatically!



Considerations to take into account:
	* Always have the Firewall rules or network segmentations correctly configured, so that the Controller
can access the rest of the equipment.
	* Never configure Ansile with ROOT, this is a big security gap.





