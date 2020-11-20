Il professore ci ha assegnato un lavoro e una macchina virtuale per poter svolgere il compito assegnatoci in laboratorio
che coinsiste nel creare implementare un web server con host virtuali, associare ad ogni sito un utente separato e attivare
il servizio FTP.

Per poter fare ciò ho dovuto eseguire dei passaggi come:

- Accedere alla macchina
- impostarsi come root: $sudo -i
- Installare l'shh: $sudo apt intsall openshh-server
- Imposto l'indirizzo ip: nano /etc/netplan/ una volta dentro lo imposto
          network:
            version: 2
            renderer: networkd
            ethernets:
              eth1:
                addresses: [10.10.10.2/24]
                gateway4: 10.10.10.1
                nameservers:
                    search: [mydomain, otherdomain]
                    addresses: [10.10.10.1, 1.1.1.1]
 









