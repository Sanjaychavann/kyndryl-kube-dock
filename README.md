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
