!!!!!!!!!!! 資料庫的部分都掛載到 /datamount

了解 mysql 版本以及密碼問題
了解 mysql 如何新增使用者
了解 postgres 如何新增使用者

//我的筆記
Dockerfile 整理。

//我的機器

//BO2

//D4SG_GCAA 機器
怎麼建立 docker 的

//BO1


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
ls
exit
ls
ls -a
docker
exit
sudo apt-get update
exit
clear
exit
curl
apt-get update
sudo apt-get update
exit
sudo apt-get update
exit
sudo -s
curl
ping 8.8.8.8
apt-get update
sudo apt-get update
sudo apt-get upgrade
sudo apt install docker.io
clear
sudo apt-get update
clear
sudo apt-get update
ping
ping 8.8.8.8
ipconfig
ifconfig
sudo ifconfig
RX packets 9222  bytes 1239318 (1.2 MB)
ifconfig 
ip -s link ls eth0
ethtool
ethtool -h
ifconfig eth0
route
ifdonfig -a
ifconfig -a
lspci
netstat
apt-get
apt-get update
sudo spt-get update
sudo apt-get update
exit
sudo apt-get update
ping 8.8.8.8
sudo apt-get update
cat /etc/apt/source.list
ls -al
sudo apt-get update
apt
apt install
sudo apt install
sudo vim /etc/ssh/
vim /etc/hosts
sudo vim /etc/hosts
vim /etc/sysctl.conf 
sudo vim /etc/sysctl.conf 
sysctl -a|grep "ipv6\|disable"
sudo reboot
exut
exit
apt install
sudo su
apt-get update
sysctl
sudo
sudo su
exit
sudo apt-get udpate
sudo apt-get update
sudo apt-get upgrade
sudo apt install docker.io
sudo systemctl start docker
sudo systemctl enable docker
docker --version
docker pull abc12207/d4sg
sudo docker pull abc12207/d4sg
sudo su
docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=P@ssw0rd" `
>>    -p 1433:1433 --name mssql `
docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=P@ssw0rd" -p 1433:1433 --name mssql -d mcr.microsoft.com/mssql/server:2019-latest
docker ps
sudo su
mysql -P 127.0.0.1
docker ps
sudo docker ps
sudo docker ps -a
docker log mssql
sudo du
sudo su
exit
sudo cat /etc/sudoers
whoami
sudo usermod -aG docker ubuntu
docker images ls
docker ps -a
adduser --help
adduser d4sggcaa
sudo su
su
su - d4sggcaa
sudo su
exit
cat /etc/ssh/sshd_config








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
   26  apt install
   27  apt-get update
   28  exit
   29  docker images -a
   30  docker run -p 80:80 -d abc12207/d4sg
   31  curl
   32  curl 127.0.0.1
   33  curl http://127.0.0.1
   34  curl http://127.0.0.1/Map
   35  docker ps
   36  docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=P@ssw0rd" -p 1433:1433 --name mssql -d mcr.microsoft.com/mssql/server:2019-latest
   37  sudo service ufw stop
   38  docker ps
   39  docker ps -a
   40  docker log mssql
   41  docker logs mssql
   42  docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=P@ssw0rd" -p 1433:1433 --name mssql -d mcr.microsoft.com/mssql/server:2019-latest
   43  docker image -a
   44  docker images -a
   45  docker rm d2520a2df464
   46  docker ps -a
   47  docker rm 1b55eefe293d
   48  docker rm c616cd6d9485
   49  docker ps -a
   50  docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=P@ssw0rd" -p 1433:1433 --name mssql -d mcr.microsoft.com/mssql/server:2019-latest
   51  docker ps -a
   52  docker logs focused_khorana
   53  exit
   54  adduser d4sggcaa
   55  cat /etc/profile
   56  cat /etc/sudoers
   57  vim /etc/sudoers
   58  exit
   59  su - d4sggcaa
   60  vim /etc/ssh/sshd_config
   61  service sshd restart
   62  vim /etc/ssh/sshd_config
   63  exit
   64  history



