# jupyter-icaycc
Configuración de jupyterhub+jupyterlab  para uso en el  ICAyCC


# Instalación Ubuntu Server
# Configuración de la red
~~~bash
cd /etc/netplan/
vim 00-installer-config.yaml 
netplan --debug apply
~~~
# Aplicación de reglas iptables 
~~~bash
/etc/iptables.local 
ln -sv /etc/iptables.local /etc/rc.local
chmod 755 /etc/rc.local
systemctl --now disable ufw.service 
~~~
# Configuración zona horaria y hostname 
~~~bash
timedatectl set-timezone America/Mexico_City
hostnamectl hostname servidor
~~~
# Instalación  certbot
~~~bash
snap refresh core
snap install --classic certbot
ln -s /snap/bin/certbot /usr/bin/certbot
certbot --nginx --agree-tos -d servidor 
~~~
# Configuración formato del historial
~~~bash
cat /etc/profile.d/history.sh 
export PROMPT_COMMAND="history -a; history -c ; history -r"
export HISTSIZE=500000
export HISTFILESIZE=500000
export HISTCONTROL="erasedups:ignoreboth"
export HISTTIMEFORMAT='%F %T '
~~~
