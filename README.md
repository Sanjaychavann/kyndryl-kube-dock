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
port mapping :

```
docker ps
   73  clear
   74  docker ps
   75  clear
   76  docker rm -f `docker ps -aq`
   77  clear
   78  docker ps
   79  docker images
   80  clear
   81  docker run -dt --name raman-c1 --hostname httpd
   82  docker run -dt --name raman-c1 --hostname webserver httpd
   83  docker exec -it raman-c1 /bin/bash
   84  docker ps
   85  netstat -tulnp
   86  clear
   87  docker ps
   88  docker inpect raman-c1
   89  docker inspect raman-c1
   90  clear
   91  curl 172.17.0.2:80
   92  clear
   93  docker ps
   94  curl 10.0.0.4:80
   95  docker run -dt --name webserver --hostname web -p 81:80 httpd
   96  docker ps
   97  curl 10.0.0.4:80
   98  curl 10.0.0.4:81
   99  docker ps
  100  curl localhost
  101  curl localhost:81
  102  curl 10.0.0.4:81
  103  curl 10.0.0.5:81
  104  netstat -tulnp

```

network :

```
 ifconfig
   16  docker network ls
   17  clear
   18  docker inspect raman-web
   19  docker network ls
   20  docker inspect network 39ef4dce3348
   21  clear
   22  docker ps
   23  docker ps -a
   24  docker netstat -tulnp
   25  docker netstat - tulnp
   26  netstat -tulnp
   27  clear
   28  docker ps -a
   29  docker run -dt --name raman-web2 -p 82:80 nginx
   30  docker ps -a
   31  docker rm -f raman-web2
   32  clear
   33  docker ps -a
   34  docker run -dt --name raman-web2 -p 81:80 nginx
   35  docker ps
   36  docker inpect raman-web2
   37  docker inspect raman-web2
   38  clear
   39  docker network ls
   40  docker inspect network 668009a247a3
   41  clear
   42  docker rm -f `docker ps -aq`
   43  docker ps -a
   44  docker run -dt --name c1 --network host httpd
   45  docker ps -a
   46  netstat -tulnp
   47  clear
   48  docker run -dt --name c2 --network host nginx
   49  docker ps
   50  docker ps -a
   51  docker logs 5f67477296ef
   52  clear
   53  docker ps
   54  docker inspect c1
   55  ifconfig
   56  clear
   57  docker ps
   58  docker run -dt --name c3 --network none httpd
   59  docker ps -a
   60  clear
   61  docker nework ls
   62  docker network ls
   63  docker network create --subnet=10.0.0.0/16 -d bridge raman-net
   64  docker network ls
   65  docker run -dt --name c4 --network raman-net nginx
   66  docker ps
   67  ifconfig
   68  clear
   69  docker ps
   70  docker inpect c4
   71  docker inspect c4
   72  docker inspect raman-net
   73  clear
   74  docker ps -a
   75  docker exec -it c4 /bin/bash
   76  docker ps -a
   77  docker start c2
   78  clear
   79  docker network --help

```
volume mapping : 1st :

```
docker rm -f `docker ps -aq`
   93  clear
   94  docker ps
   95  pwd
   96  mkdir app
   97  ls
   98  cd app
   99  ls
  100  touch hostfile
  101  ls
  102  pwd
  103  docker run -dit --name c1 -v /root/app:/data centos:7
  104  docker ps
  105  docker inspect c1 | grep -i volume
  106  docker inspect c1
  107  clear
  108  docker ps
  109  docker exec -it c1 ls /
  110  docker exec -it c1 ls /data
  111  docker exec -it c1 ls /bin/bash
  112  docker exec -it c1 /bin/bash
  113  docker ps -a
  114  docker rm -f c1
  115  pwd
  116  ld
  117  ls
  118  clear
  119  ls
  120  clear


```

vol. mapping : 2nd :

```



  121  pwd
  122  cd /var/lib/docker/
  123  ls
  124  docker images
  125  cd image/
  126  s
  127  ls
  128  cd overlay2/
  129  ls
  130  cat repositories.json
  131  clear
  132  cd ..
  133  ls
  134  cd ..
  135  ls
  136  cd volumes/
  137  ls
  138  clear
  139  docker volume ls
  140  docker volume create ramansdata
  141  docker volume ls
  142  ls
  143  cd ramansdata/
  144  ls
  145  cd _data/
  146  ls
  147  pwd
  148  clear
  149  pwd
  150  docker ps -a
  151  docker run -dit --name c1 -v ramansdata:/app/data ubuntu
  152  ls
  153  docker ps
  154  docker attach c1
  155  pwd


```
volume and port maping 2gether :

```
cd /root/
  337  clear
  338  cd /var/tmp
  339  mkdir www
  340  cd www/
  341  ls
  342  vi index.html
  343  pwd
  344  docker run -d -P --name ramanwebserver -v /var/tmp/www:/usr/share/nginx/html nginx:latest
  345  docker ps
  346  netstat -tulnp
  347  clear
  348  docker ps
  349  curl 10.0.0.4:32768
  350  ls
  351  vi index.html
  352  exit
  353  docker ps
  354  docker inpect ramanwebserver
  355  docker inspect ramanwebserver
  356  clear



<HTML>
<HEAD></HEAD>
<BODY>
<HR/>
THIS IS A TEST PAGE CREATED BY RAMAN 
<HR/>
</BODY>
</HTML>


```
resource limitaion :

```
 docker start rbweb
  957  docker ps
  958  docker stats
  959  clear
  960  docker rm -f `docker ps -aq`
  961  clear
  962  docker run -dit --name c1 -m 200M redis
  963  docker ps
  964  docker stats
  965* docker run -dt --name c2 --cpus 0.2 -m 100M cadd
  966* docker stats |
  967  docker inspect c2
  968  docker inspect c2 | grep nano
  969  docker inspect c2 | grep -i nano
  970  clear
  971  docker top c2
  972  clear
  973  docker system df
  974  docker ps
  975  docker images
  976  clear
  977  docker system prune
  978  docker images
  979  docker ps -a
  980  docker system prune -a
  981  clear
  982  docker images
  983  docker ps
  984  docker ps -a
  985  docker nework ls
  986  docker network ls
  987  docker volume ls
  988  clear
  989  docker system df

```
custom image : 1st method commit :

```
custom images : httpd is already , updated 

commit method : 

container (nothin) >> update >> commit in the form my custom image (httpd is already , updated) >>> reuse that custom image to create new containers




dockerfile  >> docker build>> image (artifact)  >> application as a conttainer



[root@56daa62c2ab9 /]# history
    1  rpm -qa | grep -i httpd
    2  ls
    3  yum update -y
    4  yum install httpd -y
    5  rpm -qa | grep -i httpd
    6  history







 docker rm -f `docker ps -aq`
  997  docker images
  998  docker rmi -f `docker images`
  999  docker images
 1000  clear
 1001  docker ps
 1002  docker images
 1003  docker run -dt --name c1 --image centos:7
 1004  docker run -dt --name c1 centos:7
 1005  docker ps
 1006  clear
 1007  docker ps
 1008  docker images
 1009  docker exec -it c1 which httpd
 1010  docker exec -it c1 /bin/bash
 1011  docker ps -a
 1012  docker images
 1013  docker ps
 1014  docker commit -m "added httpd and updated base image" -a "raman khanna" c1 ramancustomimage1
 1015  docker images
 1016  docker image history
 1017  docker image history ramancustomimage1
 1018  clear
 1019  docker images
 1020  docker rm -f `docker ps -aq`
 1021  docker images
 1022  docker ps
 1023  docker ps -a
 1024  docker rmi -f redis
 1025  docker rmi -f centos:7
 1026  clear
 1027  docker ps -a
 1028  docker images
 1029  docker run -dt --name c1 -P ramancustomimage1
 1030  docker ps
 1031  docker rm -f c1
 1032  clear
 1033  docker run -dt --name c1 ramancustomimage1
 1034  docker ps
 1035  docker images
 1036  docker exec -it c1 /bin/bash

```


Dockerfile method :

```
[root@ramanvm data]# cd /root/files/
[root@ramanvm files]# ls
Dockerfile1  Dockerfile2


[root@ramanvm files]# cat Dockerfile1
FROM centos:7
RUN yum update -y
RUN yum -y install httpd



[root@ramanvm files]# cat Dockerfile2
FROM centos:7
MAINTAINER  Raman Khanna raman.khanna@TechLanders.com
RUN mkdir /data
RUN yum update -y
RUN yum -y install httpd   php
RUN echo " TechLanders Solutions Deals in DevOps and Cloud" > /var/www/html/index.html
EXPOSE 80
VOLUME  /data
RUN echo "httpd" >> /root/.bashrc
CMD ["/bin/bash"]






pwd
 1072  ls
 1073  vi Dockerfile1
 1074  vi Dockerfile2
 1075  clear
 1076  ls
 1077  cat Dockerfile2
 1078  docker images
 1079  docker build -t ramancustomimage4 -f Dockerfile2 .
 1080  docker images
 1081  clear
 1082  docker image history ramancustomimage4
 1083  clear
 1084  docker images
 1085  docker ps
 1086  cat Dockerfile2
 1087  docker run -dt --name c2 -v "
 1088  docker volume ls
 1089  ls
 1090  ls /
 1091  cd data
 1092  cd /data
 1093  ls
 1094  clear
 1095  cat Dockerfile2
 1096  cat /root/files/Dockerfile2
 1097  docker run -dt --name c2 -v /data:/data -p 8080:80 ramancustomimage4
 1098  docker ps
 1099  docker inspect c2
 1100  ls
 1101  docker ps
 1102  docker exec -it c2 /bin/bash
 1103  ls
 1104  cat /root/files/Dockerfile2
 1105  clear
 1106  history

```

docker file copy instructions :

```
[root@ramanvm files]# cat index.html
hello people !!!


[root@ramanvm files]# cat Dockerfile3
FROM centos:7
RUN yum update -y
RUN yum install -y httpd
COPY ./index.html /var/www/html/index.html
EXPOSE 80
WORKDIR /var/www/html
CMD ["httpd","-D","FOREGROUND"]






 ls
 1113  vi Dockerfile3
 1114  ls
 1115  vi Dockerfile
 1116  cat Dockerfile3
 1117  clear
 1118  cat Dockerfile
 1119  cat Dockerfile3
 1120  docker images
 1121  docker build -t ramancustomimage5 -f Dockerfile3 .
 1122  vi index.html
 1123  ls
 1124  vi Dockerfile3
 1125  docker build -t ramancustomimage5 -f Dockerfile3 .
 1126  docker images
 1127  docker ps
 1128  docker run -dt --name c3 -P ramancustomimage5
 1129  docker ps
 1130  clear
 1131  vi index.html
 1132  cat index.html
 1133  cat Dockerfile3


```


dockerhub :

```

created dockerhub account :

dockerid , password 

created repo

logged in our dockerhub acc

taggd he image as per repo




  docker push ramancustomimage2:latest
 1143  docker login
 1144  docker push ramancustomimage2:latest
 1145  docker tag 920cbe5efd7d ramann123/kyndryl-repo:ramansimage
 1146  docker images
 1147  clear
 1148  docker images | grep raman
 1149  docker push ramann123/kyndryl-repo:ramansimage
 1150  docker tag ramancustomimage4:latest ramann123/kyndryl-repo:ramansimage2
 1151  docker images | grep raman
 1152  docker push ramann123/kyndryl-repo:ramansimage2
 1153  docker images
 1154  docker push ramann123/kyndryl-repo:tagname

```

jenkins pipeline :
```


workflow : tasks (jenkins)


jenkins : source code (github),git >>> build (maven) d >> arifacg .war file >> dockerfile >> custom image >> container


raman full access
rakesh write 
ramesh read


 jenkins : master /slave






docker images
  999  clear
 1000  cd /var/lib/
 1001  ls
 1002  cd jenkins
 1003  ls
 1004  cd workspace
 1005  ls
 1006  cd test
 1007  ls
 1008  cd ..
 1009  ls
 1010  cd ..
 1011  ls
 1012  cd ..
 1013  ls
 1014  ls -lr
 1015  clear
 1016  systemctl status jenkins
 1017  vi /usr/lib/systemd/system/jenkins.service
 1018  cat /etc/passwd
 1019  clear
 1020  vi /usr/lib/systemd/system/jenkins.service
 1021  sysemcttl daemon-reload
 1022  sysemctl daemon-reload
 1023  systemctl daemon-reload
 1024  systemctl restart jenkins
 1025  cd /root/
 1026  ls
 1027  yum install git -y
 1028  clear
 1029  java -version
 1030  clear
 1031  mvn
 1032  clear
 1033  wget https://dlcdn.apache.org/maven/maven-3/3.9.4/binaries/apache-maven-3.9.4-bin.tar.gz
 1034  ls
 1035  tar -xvzf apache-maven-3.9.4-bin.tar.gz
 1036  ls
 1037  cd apache-maven-3.9.4
 1038  ls
 1039  cd bin/
 1040  ls
 1041  ./mvn
 1042  mvn
 1043  clear
 1044  ls
 1045  cd /root/
 1046  ls
 1047  ls /usr/bin | grep ls
 1048  ls /usr/bin | grep cat
 1049  clear
 1050  ln -s /root/apache-maven-3.9.4/bin/mvn  /usr/bin/
 1051  ls -ltr /usr/bin | grep mvn
 1052  pwd
 1053  mvn
 1054  clear
 1055  mvn --version
 1056  docker ps
 1057  docker run -dt --name ramanapp ubuntu
 1058  docker ps
 1059  clear
 1060  cd /var/lib/jenkins/
 1061  ls
 1062  cd workspace/
 1063  ls
 1064  cd project-kyndryl/
 1065  ls
 1066  cd target/
 1067  ls
 1068  docker images
 1069  docker history image 0def9942a52a
 1070  docker image history 0def9942a52a
 1071  clear
 1072  docker ps
 1073  cd ..
 1074  ls
 1075  cd ..
 1076  ls
 1077  cd ..
 1078  ls
 1079  cd workspace/

```

polling :

```

 git clone https://github.com/ramannkhanna2/Devops-Maven-Docker.git
  503  ls
  504  cd Devops-Maven-Docker/
  505  ls
  506  cd src
  507  ls
  508  cd main
  509  ls
  510  cd java
  511  ls
  512  cd webapp
  513  ls
  514  vi LoginServlet.java
  515  clear
  516  git status
  517  git add .
  518  git commit -m "updated src code"
  519  git status
  520  git push origin master

```

KUBERNETES :

```


 alias k=kubectl
   12  k get nodes
   13  k get pods
   14  k get pods -A
   15  k get pods -A -o wide
   16  clear
   17  k get pods -A -o wide | grep master
   18  docker ps
   19  clear
   20  k get pods -A -o wide | grep master
   21  k get pods -A -o wide | grep worker1
   22  k get pods -A -o wide | grep worker2
   23  k get pods
   24  clear
   25  k get nodes
   26  k get pods
   27  k get pods -n kube-system
   28  k get ns
   29  clear
   30  k get pods
   31  k run ramanapp --image httpd
   32  k get pods
   33  k get pods -A
   34  clear
   35  k get pods
   36  k get pods -o wide
   37  k describe pod ramanapp
   38  clear
   39  k get pods
   40  k create ns raman
   41  k get ns
   42  k get pods -n raman
   43  clear
   44  k delete pod ramanapp
   45  clear
   46  k get pods -A
   47  clear
   48  k run ramanapp1 --image httpd -n raman
   49  k get pods
   50  k get pods -n raman
   51  k get pods -o wide -n raman


```

pods runtime :

```


root@raman-kube-master:~# cat pod.yaml
apiVersion: v1
kind: Pod
metadata:
  name: nginx
spec:
  containers:
  - name: nginx
    image: nginx:1.14.2
    ports:
    - containerPort: 80
root@raman-kube-master:~# cat multicon.yaml
apiVersion: v1
kind: Pod
metadata:
  name: multicon
spec:
  containers:
  - name: con1
    image: httpd
    ports:
    - containerPort: 80
  - name: con2
    image: redis
    ports:
    - containerPort: 6379














k delete pods --all
   58  clear
   59  k run -it centos --image centos:7 -- /bin/bash
   60  clear
   61  k get pods
   62  k delete ns raman
   63  clear
   64  ls
   65  k get pods
   66  vi pod.yaml
   67  k api-resources
   68  clear
   69  ls
   70  vi pod.yaml
   71  k create -f pod.yaml
   72  k get pods
   73  k get ns
   74  k create ns raman
   75  clear
   76  k get ns
   77  k create -f pod.yaml -n raman
   78  k get pods -n raman
   79  k get pods
   80  k get pods -o wide
   81  clear
   82  k get pods -A
   83  clear
   84  cat pod.yaml
   85  clear
   86  k get pods
   87  k delete pods --all
   88  k get pods
   89  ls
   90  k create -f pod.yaml
   91  k get pods
   92  clear
   93  k get pods
   94  k exec -it nginx -- /bin/bash
   95  clear
   96  k get pods
   97  clear
   98  cat pod.yaml
   99  vi multicon.yaml
  100  k ge pods
  101  k get pods
  102  clear
  103  k create -f multicon.yaml
  104  k get pods
  105  k get pods -o wide
  106  k exec -it multicon -c con1 -- /bin/bash
  107  k exec -it multicon -c con2 -- /bin/bash


```

