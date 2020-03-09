# ansible-create-deploer 
create deploer login on remote servers

### 1)

create key

*$ssh-keygen -t rsa -b 4096 -C "admin@linux-notes.org"*

### 2)

copy repo to /etc/ansible

### 3)

Run as follows:

*root@ansible:/etc/ansible$ ansible-playbook sudoer.yml -e "hostname=server1" -e "ansible_user=root_user" -K*

- server1 - host in /etc/ansible/hosts

- root_user - root user on remote server

- (sudoer.yml)create_user - user name will be create on remote server

sudoer.yml will do

1. create user {{create_user}} on remote server
2. add create_user to sudoer
3. copy rsa key to remote server

### 4)

test

*root@ansible:/etc/ansible$ ansible server1 -m ping*

    server1 | SUCCESS => {
      "changed": false,
      "ping": "pong"
    }


*root@ansible:/etc/ansible$ ansible server1 -a "cat /etc/shadow" -b*

    server1 | CHANGED | rc=0 >>
    root:!:18328:0:99999:7:::
    ..........
    ansible:!:18329:0:99999:7:::

