# DevOps-Project-SSH-Containers-connection
creating a Dockerfile, building an image, running two containers from that image and establish an SSH connection between the two containers, allowing the client container to SSH into the server container.



![DevOps Project](https://github.com/user-attachments/assets/4d52a32e-0e10-470e-bf7d-5d88fc2f6e4b)


Step1: Git clone the repo
--> git clone https://github.com/mostafa-shebo/DevOps-Project-SSH-Containers-connection.git

Step2: Building the Docker image through docker file
--> cd docker-file
--> vim Dockefile ----> check the dockerfile
--> docker build -t new-ssh-ubuntu:v1 .


![dockerfile](https://github.com/user-attachments/assets/f2d4744d-a148-431f-be21-2691a2465999)


** OR you can pull the image direct from docker hub through this command ###
--> docker pull mostafaabdelaziz/new-ssh-ubuntu

Step3: start the two containes (Server Side/client sied) using the image

--> docker run -d -it --name container-server new-ssh-ubuntu:v1
--> docker run -d -it --name container-client new-ssh-ubuntu:v1

Step4: configure the sshd file in cintainer-server 
--> docker exec -it  container-server bash <-- to enter the container 
--> vim sshd_config 
** NOTE : now you need to change ((#PermitRootLogin prohibit-password)) to be ((PermitRootLogin yes)) please remember to remove the hash sign (#)



![ssh-file](https://github.com/user-attachments/assets/8826728e-524e-4b8b-b980-bedf76f0adcb)


Step5: need to change the root password to be able to connect from another server
--> passwd root 
** NOTE: now you can write any new password for example 123

Step6: you need to know the container-server ip address to be able to ssh 
--> docker inspect container-server | grep IPAddress

step7: now you can ssh from container-client to container-server
--> ssh root@IP 

![image](https://github.com/user-attachments/assets/c84be71e-5382-4949-9f51-6fd62ee1e7a0)


congratultions now we complete for any info please do not hesitate to contact me.
