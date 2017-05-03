#### How to tun docker on Arch.

Got most the information here: [https://docs.docker.com/engine/installation/linux/archlinux/#starting-docker]
Initially we need to install docker directly from pacman (official repo, not AUR):

`pacman -S docker`

After it is installed you just need to run this to start it:
`sudo systemctl start docker` 

Or if you want to have it always on:
`sudo systemctl enable docker`

All the docker commands need to run on `sudo`

So if you want to check the IP address of a running container, get the container Id and run this:

`sudo docker <container_id> inspect` 

And search for something like this: 
"IPAddress": "172.17.0.2"

`172.17.0.2` is going to be ip of the first machine running, each container will generate a new IP, it should be sequencial, so the next would be `172.17.0.3`