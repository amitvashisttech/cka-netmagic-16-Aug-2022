```
 25  ./install-docker.sh
   26  ls
   27  docker version
   28  ls
   29  cd
   30  ls
   31  docker run busybox echo "Welcome to the world of Docker."
   32  docker ps
   33  docker ps -a
   34  docker run busybox echo "Welcome to the world of Docker."
   35  docker ps -a
   36  docker run busybox echo "Welcome to the world of Docker."
   37  docker ps -a
   38  docker images
   39  docker run busybox sleep 30
   40  docker run --name test-busy-sleep-1 busybox sleep 10000
   41  docker ps
   42  docker start test-busy-sleep-1
   43  docker ps
   44  docker stop test-busy-sleep-1
   45  docker ps
   46  docker ps -a
   47  docker rm test-busy-sleep-1
   48  docker ps
   49  docker ps -a
   50  docker ps -aq
   51  docker rm $(docker ps -aq)
   52  docker ps
   53  docker ps -a
   54  ls
   55  cd cka-netmagic-16-Aug-2022/
   56  ls
   57  cd 01-Docker/
   58  ls
   59  mkdir 01-Docker-Commands
   60  ls -ltr /var/lib/docker/
   61  ls -ltr /var/lib/docker/containers/
```
```
    2  docker ps -a
    3  docker ps
    4  docker ps -a
    5  docker kill test-busy-sleep-1
    6  docker ps -a
    7  docker ps
    8  docker kill 992ea428b1c4
    9  docker ps
   10  docker images
   11  docker pull amitvashist7/k8s-tiny-web
   12  docker images
   13  docker pull amitvashist7/k8s-tiny-web:2
   14  docker pull amitvashist7/k8s-tiny-web:3
   15  docker pull amitvashist7/k8s-tiny-web:4
   16  docker images
   17  docker ps
   18  docker ps -a
   19  ls
   20  docker ps
   21  docker images
   22  docker run -it ubuntu
   23  docker ps
   24  docker ps -a
   25  docker run -it ubuntu:16.04
   26  docker ps
   27  docker ps -a
   28  docker start 13d9ab2c586b
   29  docker ps
   30  docker attach 13d9ab2c586b
   31  docker ps
   32  history
   33  docker run -it ubuntu:16.04
   34  docker run -itd  ubuntu:16.04
   35  docker ps
   36  docker run -itd --name test-1  ubuntu:16.04
   37  docker ps
   38  docker attach 0~test-11~
   39  docker attach test-1
   40  docker ps
   41  docker images
   42  docker run -d --name test-2 amitvashist7/k8s-tiny-web
   43  docker ps
   44  docker inspect test-2
   45  curl 172.17.0.5
   46  ls
   47  cd cka-netmagic-16-Aug-2022/
   48  ls
   49  cd 01-Docker/
   50  ls
   51  cd 01-Docker-Commands/
```
