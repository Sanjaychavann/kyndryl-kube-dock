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

multipod :

```
k delete pods --all
  115  k get pods -A
  116  clear
  117  k get pods
  118  ls
  119  k create -f pod.yaml
  120  k get pods
  121  k get pods -A
  122  k delete pod sanjayapp -n sanjay
  123  k get pods -A
  124  k get pods -n rb
  125  k logs rbmulticon
  126  k logs rbmulticon -n rb
  127  k logs rbmulticon -c rbcon1 -n rb
  128  k logs rbmulticon -c rbcon2 -n rb







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
---
apiVersion: v1
kind: Pod
metadata:
  name: centos
spec:
  containers:
  - name: centos
    image: centos:7
    tty: true
    command: ["/bin/bash"]



```

deployment :

```

k get pods -A | wc -l
  556  clear
  557  k get pods -n raman
  558  k delete pod nginx -n raman
  559  clear
  560  k get pods
  561  clear
  562  k create deploy dep1 --image httpd --replicas 7
  563  k get pods
  564  clear
  565  k get all
  566  k delete pod dep1-849f46f8bd-xr5gc
  567  k get all
  568  clear
  569  k describe deplo dep1
  570  k describe deploy dep1
  571  clear
  572  k describe rs
  573  clear
  574  k ge pods
  575  k get pods
  576  k scale deploy dep1 --replicas 15
  577  k get pods
  578  k scale deploy dep1 --replicas 1
  579  k get pods
  580  clear
  581  k get pods


```

labels-selector :
```


root@raman-kube-master:~# cat rdeploy.yml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
  labels:
    app: nginx
spec:
  replicas: 5
  selector:
    matchLabels:
      app: rk
  template:
    metadata:
      labels:
        app: rk
    spec:
      containers:
      - name: nginx
        image: nginx:1.14.2
        ports:
        - containerPort: 80
      nodeSelector:
        env: dev
---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: httpd-deployment
  labels:
    app: httpd
spec:
  replicas: 5
  selector:
    matchLabels:
      app: rk1
  template:
    metadata:
      labels:
        app: rk1
    spec:
      containers:
      - name: httpd
        image: httpd
        ports:
        - containerPort: 80
      nodeSelector:
        env: prod






 k get pods
  585  clear
  586  k describe pod | grep -i label
  587  k describe deploy | grep -i label
  588  k describe nodes | grep -i label
  589  clear
  590  k describe rs | grep -i selector
  591  k describe pod | grep -i label
  592  k describe pod | grep -i selector
  593  cleacr
  594  clear
  595  k get pods --selector app=dep1
  596  clear
  597  ls
  598  vi rdeploy.yml
  599  k api-resources
  600  clear
  601  vi rdeploy.y
  602  vi rdeploy.yml
  603  k get deploy --selector=app=dep1
  604  vi rdeploy.yml
  605  k delete pods --all
  606  clear
  607  k get pods
  608  k delete deploy --all
  609  clear
  610  k get pods
  611  clear
  612  k get pods
  613  k create -f rdeploy.yml -n raman
  614  k get pods -n raman
  615  k get pods -o wide
  616  k delete deploy -n raman
  617  k delete deploy nginx-deployment -n raman
  618  clear
  619  k delete deploy
  620  k create -f rdeploy.yml
  621  clear
  622  k get pods -o wide
  623  k describe nodes
  624  clear
  625  k label node raman-kube-worker1 "env=prod"
  626  k describe nodes
  627  clear
  628  k label node raman-kube-worker2 "env=dev"
  629  vi rdeploy.yml
  630  k apply -f rdeploy.yml
  631  k get pods
  632  k get pods -o wide
  633  vi rdeploy.yml
  634  k apply -f rdeploy.yml
  635  k get pods -o wide --watch
  636  k get pods -o wide
  637  clear
  638  vi rdeploy.yml
  639  k apply -f rdeploy.yml
  640  k get deploy
  641  k get pods
  642  k get pods -o wide
  643  clear
  644  cat rdeploy.yml


```

hpa :


```

alias k=kubectl
 1015  k delete -f .
 1016  k get all
 1017  clear
 1018  k op nodes
 1019  k top nodes
 1020  alias k=kubectl
 1021  k top nodes
 1022  clear
 1023  ls
 1024  k get ns
 1025  k delete ns kubernetes-dashboard
 1026  k get pods
 1027  clear
 1028  k op nodes
 1029  k top nodes
 1030  clear
 1031  k describe node kube-maser
 1032  k describe node kube-master
 1033  clear
 1034  k get nodes
 1035  k get pods
 1036  k delete pods --all
 1037  clear
 1038  ls
 1039  cd k8s_metrics_server/
 1040  ls
 1041  cd deploy/
 1042  ls
 1043  clear
 1044  k get pods -A
 1045  k get hpa
 1046  k delete pod hpa
 1047  k delete pod hpa centos
 1048  k delete hpa centos
 1049  clear
 1050  k get pods
 1051  ls
 1052  cd /
 1053  cd root
 1054  pwd
 1055  vi deplloy.yml
 1056  k create -f deplloy.yml
 1057  k get pods
 1058  k autoscale deploy centos-deployment --cpu-percent 60 --min=1 --max=5
 1059  k top nodes
 1060  k top pods
 1061  k top pods -A
 1062  clear
 1063  k get pods -A
 1064  k top nodes
 1065  k top pods
 1066  k get hpa
 1067  clear
 1068  k get hpa --watch
 1069  k top pods
 1070  clear
 1071  k delete deploy --all





k get pods
 1025  k exec -it centos-deployment-c57b4c5bb-xm9mv -- /bin/bash



root@kube-master:~# cat deplloy.yml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: centos-deployment
  labels:
    app: centos
spec:
  replicas: 1
  selector:
    matchLabels:
      app: rk
  template:
    metadata:
      labels:
        app: rk
    spec:
      containers:
      - name: centos
        image: centos:7
        command: ["/bin/bash"]
        tty: true
        resources:
          requests:
            memory: "64Mi"
            cpu: "250m"
          limits:
            memory: "128Mi"
            cpu: "500m"

```

service :

```

 k delete hpa --all
  866  clear
  867  k get all
  868  clear
  869  k run c1 --image httpd
  870  k get pods
  871  k get pods -o wide
  872  k get svc
  873  clear
  874  k expose pod c1 --name extsvc --type NodePort --target-port 80 --port 80
  875  k get all
  876  k describe svc extsvc
  877  k get pods -o wide
  878  k describe pod | grep label
  879  k describe pod | grep -i label
  880  clear
  881  k get pods -A
  882  k get pods -A -o wide
  883  clear
  884  k get pods -A -o wide
  885  k get pods -o wide
  886  clear
  887  k create deploy dep1 --image nginx --replicas 2
  888  k get pods -o wide
  889  k expose deploy dep1 --name extsvcdep --type NodePort --target-port 80 --port 80
  890  k describe svc extsvcdep
  891  k create deploy dep2 --image redis --replicas 2
  892  clear
  893  k get deploy
  894  k get svc
  895  k expose deploy dep2 --name intsvc --type ClusterIP --target-port 80 --port 80
  896  k get svc
  897  k describe svc intsvc
  898  k get pods -o wide
  899  k delete svc intsvc
  900  k expose deploy dep2 --name intsvc --type ClusterIP --target-port 6379 --port 6379
  901  clear
  902  k get pods -o wide
  903  k get svc
  904  k describe svc intsvc
  905  clear
  906  k create deploy dep3 --image redis --replicas 2
  907  k expose deploy dep3 --name intsvc1 --type ClusterIP --target-port 6379 --port 6379
  908  k describe insvc1
  909  k describe intsvc1
  910  k describe svc intsvc1
  911  k get pods -o wide

```


deplomnt techniques :
```
root@raman-kube-master:~/raman# cat rdeploy.yml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: httpd-deployment
  labels:
    app: rk
spec:
  replicas: 10
  selector:
    matchLabels:
      app: rk
  template:
    metadata:
      labels:
        app: rk
    spec:
      containers:
      - name: httpd
        image: httpd
        ports:
        - containerPort: 80
root@raman-kube-master:~/raman# cat rdeploy2.yml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
  labels:
    app: rk
spec:
  replicas: 0
  selector:
    matchLabels:
      app: rk
  template:
    metadata:
      labels:
        app: rk
    spec:
      containers:
      - name: nginx
        image: nginx
        ports:
        - containerPort: 80
root@raman-kube-master:~/raman# cat service.yml
apiVersion: v1
kind: Service
metadata:
  name: raman-service
spec:
  type: NodePort
  selector:
    app: rk
  ports:
      # By default and for convenience, the `targetPort` is set to the same value as the `port` field.
    - port: 80
      targetPort: 80
      # Optional field
      # By default and for convenience, the Kubernetes control plane will allocate a port from a range (default: 30000-32767)
      nodePort: 30007









k get pods
  915  k get svc
  916  clear
  917  ls
  918  k get all
  919  k delete deploy --all
  920  k delete svc --all
  921  clear
  922  k get all
  923  clear
  924  ls
  925  vi rdeploy.yml
  926  cat rdeploy.yml
  927  vi rdeploy2.yml
  928  clear
  929  k create -f rdeploy.yml
  930  k get pods
  931  vi service.yml
  932  k describe pods | grep -i label
  933  vi service.yml
  934  k create -f service.yml
  935  k get pods
  936  k get pods -o wide
  937  k describe svc raman-service
  938  clear
  939  k create -f  rdeploy2.yml
  940  k get deploy
  941  k get svc
  942  vi service.yml
  943  cat rdeploy2.yml
  944  clear
  945  vi service.yml
  946  k apply -f service.yml
  947  clear
  948  k get svc
  949  k get deploy
  950  k scale deploy httpd-deployment --replicas 10
  951  k scale deploy httpd-deployment --replicas 0
  952  clear
  953  k get svc
  954  k get deploy
  955  k get pods
  956  k scale deploy httpd-deployment --replicas 10
  957  k scale deploy nginx-deployment --replicas 0
  958  k get pods
  959  vi rdeploy.yml
  960  vi rdeploy2.yml
  961  k apply -f rdeploy2.yml
  962  vi rdeploy2.yml
  963  k delete deploy --all
  964  clear
  965  vi rdeploy.yml
  966  vi rdeploy2.yml
  967  k create -f rdeploy.yml
  968  k create -f rdeploy2.yml
  969  vi service.yml
  970  k apply -f service.yml
  971  k get pods
  972  k scale deploy nginx-deployment --replicas 5
  973  k scale deploy httpd-deployment --replicas 5
  974  k get pods
  975  curl 10.0.0.7
  976  10.0.0.7
  977  curl 10.0.0.7:30007
  978  k scale deploy httpd-deployment --replicas 2
  979  k scale deploy nginx-deployment --replicas 8

```



rollout :

```


v1 : nginx 1.14.1 : rollin update : nginx-5cf69c89dc
v2 : nginx 1.14.2 : recreate stratergy : nginx-6ff8b45b98
v3 : nginx latest : rollin update :nginx-85d84cc48c





root@raman-kube-master:~/raman# cat rdeploy.yml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx
  labels:
    app: nginx
spec:
  replicas: 10
  #  strategy:
  # type: Recreate
  selector:
    matchLabels:
      app: rk
  template:
    metadata:
      labels:
        app: rk
    spec:
      containers:
      - name: nginx
        image: nginx:latest
        ports:
        - containerPort: 80




k delete deploy --all
 1940  clear
 1941  k get pods
 1942  k delete pods --all
 1943  clear
 1944  k get pods
 1945  clear
 1946  ls
 1947  cd raman
 1948  ls
 1949  vi rdeploy.yml
 1950  clear
 1951  cat rdeploy.yml
 1952  clear
 1953  cat rdeploy
 1954  cat rdeploy.yml
 1955  k get deplo
 1956  k get deploy
 1957  k get rs
 1958  k create -f rdeploy.yml --record=true
 1959  k rollout status deploy nginx
 1960  k get deploy
 1961  k get rs
 1962  vi rdeploy.yml
 1963  k edit deploy
 1964  vi rdeploy.yml
 1965  k create -f rdeploy.yml --record=true
 1966  k apply -f rdeploy.yml --record=true
 1967  k rollout status deploy nginx
 1968  k get deploy
 1969  k get rs
 1970  k rollout history deploy nginx
 1971  k describe deploy | grep -i image
 1972  vi rdeploy.yml
 1973  k apply -f rdeploy.yml --record=true
 1974  k rollout status deploy nginx
 1975  clear
 1976  k rollout history deploy nginx
 1977  k describe deploy | grep -i image
 1978  k rollout status deploy nginx
 1979  k get rs
 1980  k rollout undo deploy nginx --to-revision=1
 1981  k get rs
 1982  k describe deploy | grep -i image
 1983  k rollout undo deploy nginx --to-revision=2
 1984  k describe deploy | grep -i image
 1985  k get rs
 1986  vi rdeploy.yml
 1987  k api-resources
 1988  cat rdeploy.yml
 1989  clear
 1990  cat rdeploy.yml


```


dashboard :


```

k delete deploy --all
 1997  clear
 1998  k get pods
 1999  clear
 2000  k get pods -kube-system
 2001  k get pods -n kube-system
 2002  kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.7.0/aio/deploy/recommended.yaml
 2003  clear
 2004  k get ns
 2005  k get all -n kubernetes-dashboard
 2006  k edit deploy kubernetes-dashboard  -n kubernetes-dashboard
 2007  k edit svc kubernetes-dashboard -n kubernetes-dashboard
 2008  k edit deploy kubernetes-dashboard  -n kubernetes-dashboard
 2009  k edit svc kubernetes-dashboard -n kubernetes-dashboard
 2010  clear
 2011  k describe svc kubernetes-dashboard -n kubernetes-dashboard
 2012  k get pods -o wide -n kubernetes-dashboard
 2013  clear
 2014* k get
 2015  k get roles -o wide -n kubernetes-dashboard
 2016  k desribe role -n kubernetes-dashboard
 2017  k describe role -n kubernetes-dashboard
 2018  k desribe sa -n kubernetes-dashboard
 2019  k describe sa -n kubernetes-dashboard
 2020  k describe rolebinding -n kubernetes-dashboard
 2021  git clone https://raw.githubusercontent.com/kubernetes/dashboard/v2.7.0/aio/deploy
 2022  git clone https://raw.githubusercontent.com/kubernetes/dashboard/
 2023  git clone https://raw.githubusercontent.com/
 2024  clear
 2025  k get secrets -n kubernetes-dashboard
 2026  k describe secret kubernetes-dashboard-token-wkwjc  -n kubernetes-dashboard
 2027  clear
 2028  k get roles  -n kubernetes-dashboard
 2029  k get sa -n kubernetes-dashboard
 2030  k get rolebinding -n kubernetes-dashboard
 2031  k describe rolebinding -n kubernetes-dashboard
 2032  k describe role -n kubernetes-dashboard
 2033  clear
 2034  ls
 2035  vi admin.yml
 2036  k create admin.yml
 2037  k create -f admin.yml
 2038  k get sa -n kubernetes-dashboard
 2039  k get roles
 2040  k get roles -A
 2041  clear
 2042  k get clusterroles
 2043  clear
 2044  k describe clusterroles cluster-admin
 2045  vi rolebind.yml
 2046  k create -f rolebind.yml
 2047  clear
 2048  k get sa -n kubernetes
 2049  k get sa -n kubernetes-dashboard
 2050  k get secrets -n kubernetes-dashboard
 2051  k describe secret -n kubernetes-dashboard admin-user-token-x8mh9
 2052  clear




root@raman-kube-master:~/raman# cat admin.yml
apiVersion: v1
kind: ServiceAccount
metadata:
  name: admin-user
  namespace: kubernetes-dashboard
root@raman-kube-master:~/raman# cat rolebind.yml
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRoleBinding
metadata:
  name: admin-user
roleRef:
  apiGroup: rbac.authorization.k8s.io
  kind: ClusterRole
  name: cluster-admin
subjects:
- kind: ServiceAccount
  name: admin-user
  namespace: kubernetes-dashboard



```

secrets :

```

username : cmFtYW5raGFubmEK

password : cmFtYW5raGFubmExMjMK

root@raman-kube-master:~/raman# cat secret.yml
apiVersion: v1
kind: Secret
metadata:
  name: raman-secret
type: opaque
data:
  username: cmFtYW5raGFubmEK
  password: cmFtYW5raGFubmExMjMK





root@raman-kube-master:~/raman# cat secretpod.yml
apiVersion: v1
kind: Pod
metadata:
  name: secretpod1
spec:
  containers:
  - name: mypod
    image: redis
    volumeMounts:
    - name: vol1
      mountPath: "/tmp/creds"
      readOnly: true
  volumes:
  - name: vol1
    secret:
      secretName: raman-secret
root@raman-kube-master:~/raman# cat secretpod2.yml
apiVersion: v1
kind: Pod
metadata:
  name: secretpod2
spec:
  containers:
  - name: nginx
    image: nginx
    env:
    - name: SECRET_USERNAME
      valueFrom:
        secretKeyRef:
          name: raman-secret
          key: username
    - name: SECRET_PASSWORD
      valueFrom:
        secretKeyRef:
          name: raman-secret
          key: password







 k get pods
 2096  k get secrets
 2097  clear
 2098  k get secrets
 2099  clear
 2100  ls
 2101  echo 'ramankhanna' | base64
 2102  echo 'ramankhanna123' | base64
 2103  clear
 2104  vi secret.yml
 2105  k get secrets
 2106  k create -f secret.yml
 2107  k get secret
 2108  k describe secret raman-secret
 2109  ls
 2110  cat service.yml
 2111  clear
 2112  cat raman-secret.yml
 2113  cat raman-secret.yaml
 2114  ls
 2115  cat secret.yaml
 2116  cat secret.yml
 2117  k get secret
 2118  rm -rf secret.yml
 2119  clear
 2120  k get secret
 2121  vi secretpod.yml
 2122  ls
 2123  k create -f secretpod.yml
 2124  k get pods
 2125  k logs -f secretpod1
 2126  k get pods
 2127  clear
 2128  k get pods
 2129  k delete -f secretpod.yml
 2130  clear
 2131  vi secretpod.yml
 2132  k get secrets
 2133  vi secretpod.yml
 2134  k create -f secretpod.yml
 2135  k get pods
 2136  k exec -it secretpod1 -- /bin/bash
 2137  clear
 2138  k get secrets
 2139  k describe raman-secret
 2140  k describe secret raman-secret
 2141  ls
 2142  vi secretpod2.yml
 2143  k create -f secretpod2.yml
 2144  k get pods
 2145  k exec -it secretpod2 echo $SECRET_USERNAME
 2146  k exec pod -it secretpod2 echo $SECRET_USERNAME
 2147  k exec -it secretpod2 -- echo $SECRET_USERNAME
 2148  cat secretpod2.yml
 2149  k exec pod -it secretpod2 -- /bin/bash
 2150  k exec -it secretpod2 -- /bin/bash
 2151  clear
 2152  ls
 2153  cat secretpod.yml
 2154  cat secretpod2.yml




```
cm :


```

root@raman-kube-master:~/raman# cat cmpod.yml
apiVersion: v1
kind: Pod
metadata:
  name: cmprod
spec:
  containers:
  - name: mypod
    image: nginx
    volumeMounts:
    - name: cmvol
      mountPath: "/usr/share/nginx/html"
  volumes:
  - name: cmvol
    configMap:
      # Provide the name of the ConfigMap you want to mount.
      name: dev.cmap
      # An array of keys from the ConfigMap to create as files
      items:
      - key: dev.html
        path: index.html
root@raman-kube-master:~/raman# cat cmpod2.yml
apiVersion: v1
kind: Pod
metadata:
  name: cmprod2
spec:
  containers:
  - name: mypod
    image: nginx
    volumeMounts:
    - name: cmvol
      mountPath: "/usr/share/nginx/html"
  volumes:
  - name: cmvol
    configMap:
      # Provide the name of the ConfigMap you want to mount.
      name: prod.cmap
      # An array of keys from the ConfigMap to create as files
      items:
      - key: prod.html
        path: index.html





echo "hello from prod" > prod.html
 2160  ls
 2161  echo "hello from dev" > dev.html
 2162  ls
 2163  k get cm
 2164  k create cm -h
 2165  clear
 2166  k create cm prod.cmap --from-file prod.html
 2167  k get cm
 2168  k describe cm prod.cmap
 2169  k create cm dev.cmap --from-file dev.html
 2170  k get cm
 2171  clear
 2172  vi cmpod.yml
 2173  k get cm
 2174  vi cmpod.yml
 2175  k create -f cmpod.yml
 2176  k get pods
 2177  k expose pod cmprod --name cmprodsvc --type NodePort --port 80 --target-port 80
 2178  k label pod cmprod "env=prod"
 2179  k expose pod cmprod --name cmprodsvc --type NodePort --port 80 --target-port 80 --selctor "env=prod"
 2180  k expose pod cmprod --name cmprodsvc --type NodePort --port 80 --target-port 80 --selctor env=prod
 2181  k expose pod cmprod --name cmprodsvc --type NodePort --port 80 --target-port 80 --selector env=prod
 2182  clear
 2183  k get svc
 2184  k get pods
 2185  k get pods -o wide
 2186  ls
 2187  vi cmpod.yml
 2188  k apply -f cmpod.yml
 2189  vi cmpod.yml
 2190  clear
 2191  k get pods
 2192  k delete pod cmprod
 2193  ls
 2194  vi cmpod.yml
 2195  k create -f cmpod.yml
 2196  k get pods
 2197  k label pod cmprod "env=prod"
 2198  vi cmpod.yml
 2199  k apply -f cmpod.yml
 2200  clear
 2201  ls
 2202  cat cmpod.yml
 2203  vi cmpod.yml
 2204  clear
 2205  cat cmpod.yml
 2206  vi cm pod2.yml
 2207  vi cmpod2.yml
 2208  k apply -f cmpod.yml
 2209  ls
 2210  vi cmprod2.html
 2211  ls
 2212  vi cmpod2.yml
 2213  k apply -f cmpod2.yml
 2214  k get pods
 2215  k label pod cmprod2 env=prod
 2216  k get svc
 2217  k describe svc cmprodsvc
 2218  k get pods -o wide
 2219  clear
 2220  ls
 2221  cat cmpod.yml
 2222  cat cmpod2.yml



```



end2end aks :

```

 alias k=kubectl
  200  k ge nodes
  201  k get nodes
  202  az login
  203  clear
  204  az account set --subscription afc6eb08-c907-4ffa-9778-3de7391c2d4b
  205  az aks get-credentials --resource-group raman-sg --name raman-aks
  206  ls -a
  207  cd .kube
  208  ls
  209  ca config
  210  cat config
  211  clear
  212  ls
  213  cd ..
  214  ls
  215  az aks get-credentials --resource-group raman-sg --name raman-aks
  216  ls
  217  cd .kube/
  218  ls
  219  cat config
  220  clear
  221  k config view
  222  k config get-context
  223  k config get-contexts
  224  clear
  225  cd ..
  226  ls
  227  k get pods
  228  k get nodes
  229  clear
  230  k get nodes
  231  k get pods
  232  clear
  233  k get nodes
  234  clear
  235  ls
  236  git clone https://github.com/ramannkhanna2/k8s_end2end_front-backend.git
  237  ls
  238  cd k8s_end2end_front-backend
  239  ls
  240  clear
  241  ls
  242  k create -f mongodb_secrets.yml
  243  k get all
  244  k get secrets
  245  ls
  246  k create -f mongo_db.yml
  247  k get all
  248  clear
  249  ls
  250  k create -f mongo-cofigmap.yml
  251  k get cm
  252  k describe cm
  253  ls
  254  vi mongo-cofigmap.yml
  255  vi mongo-express.yml
  256  clear
  257  vi mongo-express.yml
  258  clear
  259  cat /etc/os-release
  260  clear
  261  hostnamectl set-hostname env
  262  bash
  263  clear
  264  ls
  265  alias k=kubectl
  266  k get all
  267  ls
  268  cd k8s_end2end_front-backend
  269  ls
  270  vi mongo-express.yml
  271  clear
  272  k get pods
  273  k get svc
  274  ls
  275  k create -f mongo-express.yml
  276  k get pods
  277  k get svc
  278  ls
  279  k get pods
  280  k exec -it mongo-express-5857768959-rpmtx -- /bin/bash
  281  clear
  282  k get pods
  283  k logs -f mongo-express-5857768959-rpmtx
  284  k get pods
  285  k logs mongodb-deployment-7b476c76cd-f5nwc
  286  clear
  287  k get svc
  288  k get pods
  289  k delete deploy --all
  290  k delete svc --all

```
