#Ligne de Commande Ansible et Appache2
Voici les commandes à suivre pour créer les trois noms de domaine avec Ansible et Apache2 sur un système Linux :

1- Il faut d'abord s'assurer d'avoir Ansible et Apache2 installés sur le système Linux. Si ce n'est pas le cas, installer les avec les commandes suivantes :

 Pour Ansible :
- sudo apt update
- sudo apt install ansible

Pour Appache2 : 
- sudo apt update
- sudo apt install apache2


2- Ensuite, il faut Créer un fichier d'inventaire Ansible pour spécifier les serveurs cibles. Par exemple, créer un fichier nommé "inventory.ini" avec les adresses IP des serveurs sous la section [webserver]. Nous pouvons le modifier selon nos besoins. Exemple :

[webserver]
192.168.1.10
192.168.1.11
192.168.1.12


3- Il faut créer ensuite un fichier de configuration Ansible (playbook) en utilisant un éditeur de texte. Par exemple, créer un fichier nommé "playbook.yml" et ajouter les tâches suivantes :

---
- name: Configure Apache2 virtual hosts
  hosts: webserver
  become: true
  tasks:
    - name: Enable Apache2 module
      apache2_module:
        name: <nom_du_module>   # Remplacez <nom_du_module> par le nom du module Apache2 requis pour les noms de domaine.

    - name: Create virtual host configuration
      template:
        src: templates/virtual_host.conf.j2   # Remplacez le chemin du modèle de configuration virtuelle selon vos besoins.
        dest: /etc/apache2/sites-available/{{ item }}
      loop:
        - domain1.conf
        - domain2.conf
        - domain3.conf

    - name: Enable virtual hosts
      apache2_vhost:
        state: present
        hostname: "{{ item }}"
      loop:
        - domain1
        - domain2
        - domain3


Il faut s'assurer de remplacer <nom_du_module> par le nom du module Apache2 requis pour les noms de domaine, et d'ajuster le chemin du modèle de configuration virtuelle (templates/virtual_host.conf.j2) selon la configuration.


4- Puis, créer les modèles de configuration virtuelle correspondants dans un répertoire "templates". Par exemple, créez les fichiers "virtual_host.conf.j2" avec les configurations nécessaires pour chaque nom de domaine.

5- Exécuter le playbook Ansible en utilisant la commande suivante :

ansible-playbook -i inventory.ini playbook.yml


6- Enfin, il faut Vérifier que les noms de domaine ont été créés avec succès sur les serveurs cibles en accédant aux sites web correspondants à l'aide des nouveaux noms de domaine.
 

En suivant les commandes suivantes, on devrait pouvoir créer les trois noms de domaine avec Ansible et Apache2 sur un système Linux.
