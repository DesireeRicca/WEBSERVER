Creare implementare un web server con host virtuali, associare ad ogni sito un utente separato e attivare
il  servizio FTP.

Per poter fare ciò ho dovuto eseguire dei passaggi come:

🟣 Accedere alla macchina
🟣 impostarsi come root: $sudo -i
🟣 Installare l'shh: $sudo apt intsall openshh-server
🟣 Imposto l'indirizzo ip: nano /etc/netplan/ una volta dentro lo imposto
           - network:
            - version: 2
            - renderer: networkd
            - ethernets:
              - eth1:
                - addresses: [10.10.10.2/24]
                - gateway4: 10.10.10.1
                - nameservers:
                    - search: [mydomain, otherdomain]
                    - addresses: [10.10.10.1, 1.1.1.1]
                    
🟣 Installo apache2: sudo apt install apache2
🟣 Creo un utente: sudo useradd -s /bin/bash -d /var/www/sitoA -m usersitoA
🟣 Imposto la password a sitoA: sudo passwd usersitoA
🟣 Installo vsftpd: sudo apt-get install vsftpd
🟣 Configuro vsftp: sudo nano /etc/vsftpd.conf
🟣 Una volta dentro configuro vsftp: 
*listen=yes

*listen_ipv6=NO*

*anonymous_enable=NO*

*local_enable=YES*

*write_enable=YES*

*local_umask=022*

*dirmessage_enable=YES*

*use_localtime=YES*

*xferlog_enable=YES*

*connect_from_port_20=YES*

*xferlog_file=/var/log/vsftpd.log*

*xferlog_std_format=YES*

*ftpd_banner=Welcome to our  FTP service.*

*chroot_local_user=YES*

*local_root=/var/www/$USER*

*user_sub_token=$USER*

*allow_writeable_chroot=YES*

*secure_chroot_dir=/var/run/vsftpd/empty*

*pam_service_name=vsftpd*

*rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem*

*rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key*

*ssl_enable=NO*

*session_support=YES*

*log_ftp_protocol=YES*


Una volta configurato il tutto apriamo FileZilla e verifichiamo se possiamo creare una cartella, se funziona tutto senza dare problemi si sono eseguti corettamente i passaggi.


 
 









