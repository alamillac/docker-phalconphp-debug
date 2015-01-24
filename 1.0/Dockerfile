# phalconphp-debug
#
# VERSION               1.0

FROM     alamilla/phalconphp
MAINTAINER Andres F. Lamilla, "alamilla@gmail.com"

# actualizacion repositorios
RUN apt-get update

# instalacion de los paquetes necesarios para la app
RUN DEBIAN_FRONTEND=noninteractive apt-get install -y rsync openssh-server vim tmux

RUN mkdir /var/run/sshd

# se adicionan los archivos de configuracion
ADD src/ssh.sv.conf /etc/supervisor/conf.d/ssh.sv.conf
ADD src/start_ssh.sh /usr/local/bin/start_ssh.sh

RUN chmod +x /usr/local/bin/*.sh

# se crea un usuario para acceder al sistema
RUN useradd -g sudo ubuntu

# se establece una password de root
RUN echo 'ubuntu:ubuntu' | chpasswd

# se habilita el puerto 80, el 22 y el script de inicio
EXPOSE 80
EXPOSE 22
CMD ["/usr/local/bin/run.sh"]
