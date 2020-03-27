# ansible-keeproxycluster-onaws
Produzione di un cluster HAproxy con ElasticIP gestito da keepalive su AWS

# Prerequisiti AWS
Assicurarsi che sull'ambiente AWS sia presente:

* Service Group con regole Inbound aperte per la connessione SSH
* che sia stato dato un ip alla scheda di rete primaria di ogni nodo
* che sia stata creato un ElasticIP non associato ad alcun nodo

Sul server Ansible:

* Fare il download con git clone
* All'interno dell'inventory path inserire la "chiave.pem" per l'accesso in SSH
* All'interno dell'inventory path inserire il pacchetto awscliv2.zip
* Modificare il file hosts del server ansible aggiungendo gli ip degli host da raggiungere e nominandoli come specificato in keeproxy.hosts

# Installazione e configurazione iniziale dei nodi 

* verificare la variabili in group_vars/all.yml
* se necessario modificare i valori delle variabili in base al proprio ambiente

lanciare il playbook ansible con il comando:

* ansible-playbook -i keeproxy.hosts keeproxy.yml --key-file=./chiave.pem --user=centos
