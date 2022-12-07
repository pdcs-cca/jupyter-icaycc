# jupyter-icaycc
Configuración de jupyterhub+jupyterlab  para uso en el  ICAyCC


# Instalación Ubuntu Server
# Configuración de la red
cd /etc/netplan/
vim 00-installer-config.yaml 
netplan --debug apply

# Aplicación de reglas iptables 
/etc/iptables.local 
ln -sv /etc/iptables.local /etc/rc.local
chmod 755 /etc/rc.local
systemctl --now disable ufw.service 

# Configuración zona horaria y hostname 
timedatectl set-timezone America/Mexico_City
hostnamectl hostname emrys.atmosfera.unam.mx

# Instalación  certbot
snap refresh core
snap install --classic certbot
ln -s /snap/bin/certbot /usr/bin/certbot
certbot --nginx --agree-tos -d emrys.atmosfera.unam.mx

# Configuración formato del historial
