# Docker Learning Note

`docker version`: docker 的 version。  
`sudo usermod -a -G docker <username>`: 設定 user 可以執行 Docker。好像下一次登入才會生效。(亦可寫成`sudo usermod -aG docker ubuntu`)  
`sudo service docker start`: 啟動docker服務。  

---

## Note

### YT - NetworkChuck

- **[you need to learn Docker RIGHT NOW!! // Docker Containers 101](https://www.youtube.com/watch?v=eGz9DS-aIeY)**

```{bash}
docker pull <image_name_from_dockerhub>
dpcker pull <image_name_from_dockerhub_url>:<tag_name> //例如docker pull thenetworkchuck/nccoffee:frenchpress
docker run -d -t --name <container_name> <image_name>
docker ps  //see running docker containers
docker ps -a  //顯示有在run以及exited的container。
docker exec -it <container_name or container_ID> bash //bash mode 進入操控 container
docker exec -it <container_name or container_ID> sh //shell mode 進入操控 container
docker stop <cintainer_name or container_ID>  //和container exited不一樣。
docker start <container_name or container_ID>
docker stats  //觀看目前每個container的資源使用情況，包含CPU、Memory等等。

//以下是 docker pull centos 的資訊
Using default tag: latest  //從DockerHub下載的tag
latest: Pulling from library/centos
6910e5a164f7: Pull complete
Digest: sha256:4062bbdd1bb0801b0aa38e0f83dece70fb7a5e9bce223423a68de2d8b784b43b
Status: Downloaded newer image for centos:latest
docker.io/library/centos:latest
```

NGINX，是web server software，我猜和Apache很像。

### D4SGxGCAA - SQL SERVER

```{bash}
docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=P@ssw0rd" -p 1433:1433 --name mssql -d mcr.microsoft.com/mssql/server:2019-latest
```

---

## tutroial

### phoenixnap website

- [How to Install Docker On Ubuntu 18.04 {2020 Tutorial}](https://phoenixnap.com/kb/how-to-install-docker-on-ubuntu-18-04)

There are two versions of Docker – Docker CE (Community Edition) and Docker EE (Enterprise Edition).  
If you have a small-scale project, or you're just learning, you will want to use Docker CE.

**check unbuntu version:**

```{bash}
lsb_release -d
lsb_release -a
cat /etc/issue
cat /etc/os-release
hostnamectl 
```

--

**在 ubuntu 上安裝 Docker:**

```{bash}
sudo apt-get update
sudo apt-get remove docker docker-engine docker.io
sudo apt install docker.io
systemctl --version
sudo systemctl start docker
sudo systemctl enable docker
```

Older versions of the Docker binary were called docker or docker-engine or docker-io  
docker-io package is still the name used by Debian/Ubuntu for the docker release provided on their official repos.  
docker-ce is a certified release provided directly by docker.com and can also be built from source.  
Main reason for using the name docker-io on Debian/Ubuntu platform was to avoid a name conflict with docker system-tray binary.

> 較舊版本的Docker二進製文件稱為docker或docker-engine或docker-io
> docker-io軟件包仍然是Debian / Ubuntu在其官方repos上提供的docker版本所使用的名稱。
> docker-ce是由docker.com直接提供的認證版本，也可以從source構建。
> 在Debian / Ubuntu平台上使用名稱docker-io的主要原因是為了避免與docker系統托盤二進製文件發生名稱衝突。

**systemctl註解:**

> 透過 systemctl 管理單一服務 (service unit) 的啟動/開機啟動與觀察狀態。
> systemd 這個啟動服務的機制，主要是透過一隻名為 systemctl 的指令來處理的。
> systemd 就是僅有 systemctl 這個指令來處理而已呦！所以全部的行為都得要使用 systemctl 的意思啦！

---

## Docker-doc

- [Docker overview | Docker Documentation](https://docs.docker.com/get-started/overview/)

```{bash}
//page: Docker overview
sudo docker run -i -t ubuntu /bin/bash

//-i, --interactive                    Keep STDIN open even if not attached。讓容器的標準輸入保持打開。
//-t, --tty                            Allocate a pseudo-TTY。讓Docker分配一個虛擬終端（pseudo-tty）並綁定到容器的標準輸入上
//此指令會進入container中，前面會有container ID。
//-d, --detach                         Run container in background and print container ID
```

1. **If you do not have the ubuntu image locally, Docker pulls it from your configured registry, as though you had run docker pull ubuntu manually.**

2. Docker creates a new container, as though you had run a docker container create command manually.

3. **Docker allocates a read-write filesystem to the container, as its final layer. This allows a running container to create or modify files and directories in its local filesystem.**

4. Docker creates a network interface to connect the container to the default network, since you did not specify any networking options. This includes assigning an IP address to the container. **By default, containers can connect to external networks using the host machine's network connection.**

5. **Docker starts the container and executes /bin/bash. Because the container is running interactively and attached to your terminal (due to the -i and -t flags), you can provide input using your keyboard while the output is logged to your terminal.**

6. **When you type exit to terminate the /bin/bash command, the container stops but is not removed. You can start it again or remove it.**

--

- [程式扎記: Docker Practice - Container](http://puremonkey2010.blogspot.com/2015/05/docker-practice-container.html)

當利用 docker run 來建立容器時，Docker 在後臺執行的標準操作包括：

1. 檢查本地是否存在指定的映像檔，不存在就從公有倉庫下載
2. 利用映像檔建立並啟動一個容器
3. 分配一個檔案系統，並在唯讀的映像檔層外面掛載一層可讀寫層
4. 從宿主主機設定的網路橋界面中橋接一個虛擬埠到容器中去
5. 從位址池中設定一個 ip 位址給容器
6. 執行使用者指定的應用程式
7. 執行完畢後容器被終止

```{bash}
docker export <conyainer_name or container_ID> > <XXX.tar>
```

---

## Command

- docker run
  - i
  - d
  - t

- docker pull

- docker load

- docker import

- docker ps
  - a
  - q

- docker start <container name or container ID>

- docker stop <container name or container ID>

- docker rm <container name or container ID>

- docker exec <container name or container ID>
  - i
  - t
  - bash|sh: 用甚麼 command mode 去進入操作 container。

docker logs <container name or container ID>
