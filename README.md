We can do this task on ubuntu machine and do practice of all aspects of docker 

Steps To proceed:-
Launch one ec2 instance of ubuntu with t2.micro once done will fire some commands

ssh -i <keyname.pem> ubuntu@<public-ip>

sudo apt update ------> To update latest repos

sudo apt install docker.io -----> Install docker 

docker version ------> check docker version 

but you can see the error like this Got permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Get http://%2Fvar%2Frun%2Fdocker.sock/v1.24/version: dial unix /var/run/docker.sock: connect: permission denied

to resolve this follow the steps

sudo usermod -aG docker $USER -----> Add your user to the docker group.

now exit from server and reconnect again like this
ssh -i <keyname.pem> ubuntu@<public-ip>

sudo systemctl enable docker -----> enable docker 

Explore Docker Hub:- 

Sign in to https://hub.docker.com
At the top of the page, search for "httpd".
In the left-hand menu, filter for Application Infrastructure, and Official Images.
Select the httpd project.
At the top of the page, click the Tags tab.
Under latest, select linux/amd64.
Back in the list of available images, select nginx
Review the How to use this image section.

Pull the httpd image and try to run 

ubuntu@ip-172-31-25-151:~$ docker pull httpd:2.4

check docker image

ubuntu@ip-172-31-25-151:~$ docker images
REPOSITORY   TAG       IMAGE ID       CREATED        SIZE
httpd        2.4       d16a51d08814   30 hours ago   145MB

ubuntu@ip-172-31-25-151:~$ docker run --name httpd -p 8080:80 -d httpd:2.4
0f87d2b940d28e2d6bae9d28834d7e4ae492f6a5cd5925ad9306ebb1da924697


