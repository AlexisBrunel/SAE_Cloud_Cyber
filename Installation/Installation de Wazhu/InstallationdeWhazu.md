# Installation de Wazhu 

### Téléchargement de la machine  



        https://nextcloud.iutbeziers.fr/s/7Epd4NBPK6N92PF


Décompression du fichier 

    tar -xvf wazuh-4.5.0.ova

Conversion vmdk -> qcow2


    qemu-img convert -O qcow2 wazuh-4.5.0-disk-1.vmdk wazuh.qcow2


Puis nouvelle machine :  



![Alt text](Wazuhinstall%C3%A9.png)

