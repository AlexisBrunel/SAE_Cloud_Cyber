# Lancement du script pour déployer les SRV(S) : 

    ansible-playbook -i inventory.ini SRV_install_wazuh.yml

# Lancement du script pour déployer les DC(s)

    ansible-playbook -i inventory.ini DC_install_wazuh.yml


