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
