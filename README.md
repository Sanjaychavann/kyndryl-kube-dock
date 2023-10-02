```
================================================================


docker cli : commands >> 

docker daemon : service whch interacts with software itself

docker engine


----
 setup done :

 cat /etc/os-release
    3  clear
    4  sudo yum install -y yum-utils
    5  sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
    6  sudo yum install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
    7  clear
    8  docker ps
    9  clear
   10  systemctl status docker
   11  systemctl star docker
   12  systemctl start docker
   13  systemctl status docker
   14  clear
   15  docker ps
   16  clear
   17  docker ps
   18  ps -ef | grep -i docker
   19  history


----------------------------------------------


```
docker runime :

```
cntrl +p+q

-i : interactiveness , -d : detach mode ,-t : terminal


-it :
docker run -it --name c1 centos:7

-dt :
docker run -dt --name c2 centos:7

-d
docker run -d --name c3 httpd


-dit
 docker run -dit --name c4 ubuntu








attach / exec command : for connecting ...



container runtime :

hostnamectl
sudo -i
    2  ssh ramanvm@pubIP
    3  exit
    4  clear
    5  docker images
    6  docker ps
    7  docker run -it --name c1 centos:7
    8  docker ps
    9  docker ps -a
   10  docker start c1
   11  docker ps
   12  docker images
   13  docker run -dt --name c2 centos:7
   14  docker ps
   15  clear
   16  docker attach c1
   17  docker start c1
   18  docker ps
   19  docker attach c2
   23  docker docker ps -a
   24  clear
   25  docker ps -a
   26  docker start c3
   27  docker ps
   28  docker run -dit --name c4 httpd
   29  docker ps
   30  docker images
   31  docker attach c4
   32  docker rm -f c4
   33  clear
   34  docker run -dit --name c4 ubuntu
   35  docker ps
   36  docker attach c4
   37  docker ps -a
   38  docker start c4
   39  docker exec -it c3 /bin/bash
   40  docker start c3
   41  docker exec -it c3 ls
   42  docker exec -it c3 mkdir raman
   43  docker exec -it c3 /bin/bash
   44  docker start c3
   45  docker ps
   46  docker exec -it c2 /bin/bash
   47  docker start c2
   48  clear
   49  docker ps -a
   50  docker stop c1
   51  docker ps
   52  docker ps -a
   53  docker kill c1
   54  docker start c1
   55  docker ps
   56  docker c3
   57  docker kill c3
   58  docker ps -a
   59  docker rm c3
   60  docker ps
   61  docker ps -a
   62  docker rm c1
   63  docker rm -f c1
   64  docker ps -a
   65  docker images
   66  clear
   67  dcoker ps
   68  doker ps
   69  docker ps
   70  docker stop c2
   71  docker kill c4
   72  docker ps -a
   73  history
   74  docker pull ubuntu:22.04
   75  docker images


```
