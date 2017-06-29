



Docker ssh

```
sudo docker exec -it 08c02edc3fbd  /bin/bash
```



Install SSH

```
apt-get update
apt-get install openssh-client
ssh -V
ls -a ~/.ssh
ls -a ~/.ssh

ssh-keygen 
 ls -a ~/.ssh
 ps -e | grep [s]sh-agent
 ssh-agent /bin/bash
 ssh-add ~/.ssh/id_rsa
 ssh-add -l 
 
```

Install Git

```
apt-get install git-all
```



