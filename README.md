# VirtualHosts
# Création de trois domaines Avec Ansible Et Appache2
Voici un récapitulatif plus clair des étapes pour créer trois noms de domaine avec Ansible et Apache2 sur un système Linux :

1- Il faut s'assurez d'avoir Ansible et Apache2 installés sur votre système Linux.

2- Créer un fichier d'inventaire Ansible pour spécifier les serveurs cibles.

3- Créer un fichier de configuration Ansible (playbook) qui détaille les tâches à effectuer.

4- Utiliser le module "apache2_module" pour activer le module Apache2 requis.

5- Ajouter une tâche pour créer les fichiers de configuration virtuels des noms de domaine à l'aide du module "template".

6- Ajouter une autre tâche pour activer les fichiers de configuration virtuels en utilisant le module "apache2_vhost".

7- Exécuter le playbook Ansible en spécifiant le fichier d'inventaire et le playbook à utiliser.

8- Vérifier que les noms de domaine ont été créés avec succès sur les serveurs cibles.

En suivant ces étapes, on peut automatiser la création de trois noms de domaine avec Ansible et Apache2 sur un système Linux.
