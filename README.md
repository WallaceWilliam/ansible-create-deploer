# ansible-create-deploer 
create deploer login on remote servers

1)

create key

ssh-keygen -t rsa -b 4096

2)

copy repo to /etc/ansible

3)

Run as follows:

root@ansible:/etc/ansible$ ansible-playbook sudoer.yml -e "hostname=server1" -e "ansible_user=root_user" -K

server1 - host in /etc/ansible/hosts

root_user - root user on remote server

(sudoer.yml)create_user - user name will be create on remote server

sudoer.yml will do

- create user {{create_user}} on remote server

- add create_user to sudoer

- copy rsa key to remote server

4)

test

root@ansible:/etc/ansible$ ansible server2 -m ping

root@ansible:/etc/ansible$ ansible server1 -a "cat /etc/shadow" -b


