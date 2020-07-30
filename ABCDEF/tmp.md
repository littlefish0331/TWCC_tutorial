對方怎麼建立 mysql 的!!!??!?!?
為何連線都不會有問題????
dockerfile學習一下，去官往先複習


ls
sudo vim /etc/ssh/
sudo su
exit
ls
vim /etc/hosts
sudo vim /etc/hosts
exit
sudo vim /etc/hosts
vim /etc/sysctl.conf 
sudo vim /etc/sysctl.conf 
sudo reboot
sysctl 
sysctl -a|grep "ipv6\|disable"
sysctl -a|grep "ipv6\|disable\| 1"
sudo vim /etc/apt/sources.list
sudo apt-get install zsh
sudo apt-get remove zsh
sudo vim /etc/apt/sources.list
sudo apt-get install zsh
sudo apt-get update
sudo apt-get install zsh
sudo apt-get remove zsh
sudo apt-get install zsh
sudo apt-get remove zsh
exit
date
exit
apt-get install ntp
sudo apt-get install ntp
sudo apt-get install ntpd
sudo apt-get install ntp
sudo apt-get update
sudo apt-get install ntp
ls
vim /etc/apt/sources.list
exit
ping free.nchc.org.tw
vim /etc/apt/sources.list
sudo vim /etc/apt/sources.list
sudo apt-get update
sudo apt-get install ntp
sudo ntpdate 140.110.16.1
sudo apt-get install ntpdate
sudo ntpdate 140.110.16.1
systemctl stop ntp
sudo systemctl stop ntp
sudo ntpdate 140.110.16.1
sudo yum update -y
tmux
exit
sudo apt-get upgrade -y
date
sudo dpkg-reconfigure tzdata 
date
vim /etc/ntp.conf 
sudo vim /etc/ntp.conf 
sudo systemctl restart ntp
sudo systemctl status ntp
vim /etc/hosts
hostname
vim /etc/hosts
sudo vim /etc/hosts
ntpq -p
cat /etc/hosts
sudo vim /etc/apt/sources.list
sudo su
cat /etc/apt/sources.list
exit
docker-compose version
sudo docker-compose version
sudo -i
cd sudo chmod +x /usr/local/bin/docker-compose
cd /dev/shm
ls
cd bigobject/
docker-compose up -d
docker ps
sudo groupadd docker
sudo usermod -aG docker ubuntu
newgrp docker
docker ps
docker-compose version
docker-compose up -d
docker ps
docker version
sudo reboot
ls
sudo -i
cd /dev/shm
ls
./get-docker.sh
docker version
cd bigobject/
ls
docker-compose up -d
snap remove docker
sudo snap remove docker
sudo -i
LS
ls
docker ps
cd /dev/shm/bigobject
l
cd /dev/shm/
ls
mkdir bigobject
ls
cd bigobject/
ls
docker-compose up -d
docker p
docker ps
ls
cd home/
ls
cd /home
ls
cd ubuntu/
ls
mv/home/cs/license /dev/shm/bigobject/config
mv/home/cs/ license /dev/shm/bigobject/config
;s
ls
mv * /dev/shm/bigobject/config
sudo mv * /dev/shm/bigobject/config
cd /dev/shm/bigobject/config
ls
mysql -h 127.0.0.1 -P 3306
sudo apt install mysql-client-core-5.7
mysql -h 127.0.0.1 -P 3306
mysql -h 127.0.0.1 -P 13301
docker ps
docker restart NCHC_master
docker restart NCHC_client 
mysql -h 127.0.0.1 -P 13301
ls
cd /dev/shm/bigobject/
ls
cd config/
ls
docker ps -a
df
df -h
docker --version
sudo -i
ls
df -h
blkid
vi /etc/fstab
blkid
fdisk -l
sudo fdisk -l
sudo -i
docker ps
docker stop some-mariadb && docker rm some-mariadb
docker ps
docker run --name some-mariadb -p 3308:3306 -e MYSQL_ROOT_PASSWORD=NCHC-COVID19 -dit mariadb
docker logs some-postgres 
docker exec -it some-postgres bash
ls
docker ps
docker exec -it some-mariadb bash
df -h
sudo -i
ls
sudo -i
cd /data2/bigobject/
ls
docker-compose up -d
ls
cd file
ls
cd /home/ubuntu/
ls
mv license /data2/bigobject/config/
sudo mv license /data2/bigobject/config/
cd /data2/bigobject/config/
ls
mysql -h 127.0.0.1 -P 3306
docker ps
docker restart NCHC_master
docker restart NCHC_client
mysql -h 127.0.0.1 -P 3306
cd ..
cd data2
cd /home
cd /data2/bigobject/
ls
cp user.csv /data2/bigobject/file/
ls
cd ../
ls
chmod 777 bigobject/ -R
sudo chmod 777 bigobject/ -R
ls
sudo chmod 666 bigobject/ -R
ls
sudo chmod 600 bigobject/ -R
ls
cd bigobject/
ls
cd bigobject/
ls
sudo chmod 666 bigobject/ -R
ls
sudo chmod 664 bigobject/ -R
ls
cd bigobject/
ls
sudo -i
cd /
cd data2/bigobject/
ls -al
sudo chmod 664 file/
ls -al
cd /data2/bigobject/file/
sudo cd /data2/bigobject/file/
sudo -i
mysql -h 127.0.0.1 -P 3306
sudo -i
cd /data2/bigobject/file/
ls
sudo -i
docker ps
docker stop some-mariadb && docker rm some-mariadb
docker run --name some-mariadb -v /my/custom:/etc/mysql/conf.d -e MYSQL_ROOT_PASSWORD=my-secret-pw -d mariadb:tag
adocker run --name some-mariadb -v /my/custom:/etc/mysql/conf.d -e MYSQL_ROOT_PASSWORD=NCHC-COVID19 -dit mariadb
mkdir /data2/mariadb-volume
sudo mkdir /data2/mariadb
sudo mkdri /data2/postgres
sudo mkdir /data2/postgres
docker run --name some-mariadb -v /data2/mariadb:/var/lib/mysql -p 3308:3006 -e MYSQL_ROOT_PASSWORD=NCHC-COVID19 -dit mariadb
docker ps
docker stop some-postgres && docker rm some-postgres
docker run --name some-postgres -v /data2/postgres:/var/lib/postgresql -p 3307:3006 -e MYSQL_ROOT_PASSWORD=NCHC-COVID19 -dit postgres
docker ps
docker ps -a
docker run --name some-postgres -v /data2/postgres:/var/lib/postgresql -p 3307:3006 -e POSTGRES_PAWWSORD=NCHC-COVID19 -e PGDATA=/var/lib/postgres/data/pgdata -dit postgres
docker rm some-postgres
docker run --name some-postgres -v /data2/postgres:/var/lib/postgresql -p 3307:3006 -e POSTGRES_PAWWSORD=NCHC-COVID19 -e PGDATA=/var/lib/postgres/data/pgdata -dit postgres
docker ps
docker run --name some-postgres -v /data2/postgres:/var/lib/postgresql -p 3307:3006 -e POSTGRES_PASSWORD=NCHC-COVID19 -e PGDATA=/var/lib/postgres/data/pgdata -dit postgres
docker rm some-postgres
docker run --name some-postgres -v /data2/postgres:/var/lib/postgresql -p 3307:3006 -e POSTGRES_PASSWORD=NCHC-COVID19 -e PGDATA=/var/lib/postgres/data/pgdata -dit postgres
docker ps
docker exec -it some-mariadb bash
docker ps
docker stop some-mariadb && docker rm some-mariadb
docker run --name some-postgres -v /data2/postgres:/var/lib/postgresql -p 3307:3306 -e POSTGRES_PASSWORD=NCHC-COVID19 -e PGDATA=/var/lib/postgres/data/pgdata -dit postgres
docker stop some-postgres && docker rm $_
docker run --name some-postgres -v /data2/postgres:/var/lib/postgresql -p 3307:3306 -e POSTGRES_PASSWORD=NCHC-COVID19 -e PGDATA=/var/lib/postgres/data/pgdata -dit postgres
docker run --name some-postgres -v /data2/postgres:/var/lib/postgresql -p 3307:3306 -e POSTGRES_PASSWORD=NCHC-COVID19 -e PGDATA=//data/pgdata -dit mariadb
docker run --name some-mariadb -v /data2/mariadb/:/var/lib/mysql -p 3308:3306 -e MYSQL_ROOT_PASSWORD=NCHC-COVID19 -d mariadb
docker ps
docker exec -it some-mariadb bash
docker exec -it some-postgres bash
cd /
ls -al
cd data2/
ls -al
cd bigobject/
ls -al
cd ..
cd BOdb/
ls -al
cd ..
rm -r BOdb/
sudo rm -r BOdb/
cd lost+found/
vi /etc/fstab
sudo -i
exit














    1  vim /etc/ssh/sshd_config
    2  systemctl |grep ssh
    3  systemctl restart ssh
    4  exit
    5  apt upgrade
    6  apt-get upgrade
    7  apt-get install zip
    8  apt-get update
    9  vim /etc/apt/sources.list
   10  apt-get update
   11  exit
   12  sudo vi /etc/systemd/system/rc-local.service
   13  sudo vi /etc/rc.local
   14  sudo chmod +x /etc/rc.local
   15  sudo systemctl enable rc-local
   16  sudo systemctl start rc-local.service
   17  sudo systemctl status rc-local.service
   18  sudo vi /etc/rc.local
   19  sudo systemctl status rc-local.service
   20  sudo systemctl start rc-local.service
   21  sudo systemctl status rc-local.service
   22  sudo vi /etc/rc.local
   23  sudo systemctl start rc-local.service
   24  sudo systemctl status rc-local.service
   25  reboot
   26  ls
   27  cd ../
   28  ls
   29  cd dev/
   30  ls
   31  cd vdb/
   32  df- h
   33  ls
   34  cd
   35  ls
   36  cd ../
   37  ls
   38  df -h
   39  cd /dev
   40  ls
   41  cd disk
   42  ls
   43  cd ../
   44  ls
   45  df -h
   46  cd shm/
   47  ls
   48  curl -fsSL https://get.docker.com -o get-docker.sh
   49  ls
   50  chomod a+x *
   51  chmod a+x get-docker.sh
   52  ls
   53  exit
   54  docker-compose version
   55  cd /dev/shm
   56  ls
   57  sudo chmod +x /usr/local/bin/docker-compose
   58  docker-compose version
   59  exit
   60  snap remove docker
   61  rm -R /var/lib/docker
   62  sudo apt-get remove docker docker-engine docker.io
   63  cd /dev/
   64  cd shm/
   65  ls
   66  ./get-docker.sh
   67  docker version
   68  docker-compose version
   69  sudo curl -L "https://github.com/docker/compose/releases/download/1.26.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
   70  history
   71  exit
   72  fdisk /dev/vdb
   73  mkfs -t ext4 /dev/vdb
   74  blkid
   75  vi /etc/fstab
   76  cd ~
   77  ls
   78  cd /
   79  ls
   80  mkdir /data2
   81  vi /etc/fstab
   82  mount /data2
   83  df -h
   84  docker pull mariadb:latest
   85  docker pull postgres
   86  docker run -dit --name some-postgres -p 3307:3306 -e POSTGRES_PASSWORD=NCHC-COVID19 postgres
   87  docker run -dit --name some-mariadb -p 3308:3306 -e MYSQL_ROOT_PASSWORD=NCHC-COVID19 mariadb
   88  docker exec -it some-mariadb bash
   89  cd /
   90  cd data2/
   91  mkdir BOdb/
   92  ls -al
   93  ls
   94  cd ../
   95  ls
   96  df -h
   97  cd /dev/shm
   98  ls
   99  cd bigobject/
  100  ls
  101  docker-compose down
  102  cd ../
  103  mv -r bigobject/ /data2
  104  mv -r bigobject /data2/
  105  mv bigobject /data2/
  106  cd /data2/bigobject
  107  ls
  108  exit
  109  ls
  110  cd /data2/bigobject/
  111  ls
  112  cp user.csv /data2/bigobject/file/
  113  cd file/
  114  ls
  115  mysql -h 127.0.0.1 -P 3306
  116  cd /data2/bigobject/file/
  117  ls
  118  EXIT
  119  exit
  120  cd /data2/bigobject/
  121  ls
  122  chmod 644 *
  123  chown ubuntu /data2/bigobject/
  124  chown ubuntu /data2/bigobject
  125  chown -R ubuntu /data2/bigobject
  126  exit
  127  cd /data2/bigobject/
  128  ls
  129  history
  130  exit
  131  $(uname -s)
  132  date
  133  vim /etc/ntp.conf
  134  docker ps -a
  135  docker-compose version
  136  apt list | grep ^docker
  137  exit
  138  history
