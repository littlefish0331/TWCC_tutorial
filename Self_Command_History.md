# Self Command History

這裡存放自己操作成功，並整理過後的指令(包括 bash 和 docker)。  
基本上照著做就可以到達同樣效果。  

簡單來說就是我的指令記事本啦XD~  
所以這邊都是從其他的 .md 檔複製過來之後，再做一點排版和補充。

<!-- TOC -->

- [Self Command History](#self-command-history)
  - [basic](#basic)
    - [歷史資訊清除](#歷史資訊清除)
    - [重開機](#重開機)
    - [已經安裝的套件](#已經安裝的套件)
    - [磁碟使用的初始狀況](#磁碟使用的初始狀況)
    - [權限修改](#權限修改)
    - [顯示目錄下-檔案-編碼-結尾換行符號](#顯示目錄下-檔案-編碼-結尾換行符號)
    - [su 最高權限者](#su-最高權限者)
    - [Others](#others)
    - [修改 ssh 登入](#修改-ssh-登入)
    - [TWCC-port connect](#twcc-port-connect)
  - [mount/umount Disk](#mountumount-disk)
    - [掛載狀況](#掛載狀況)
    - [格式化、掛載、卸除](#格式化掛載卸除)
    - [設定開機自動掛載](#設定開機自動掛載)
  - [Docker](#docker)
    - [下載docker](#下載docker)
    - [連結 docker hub](#連結-docker-hub)
    - [下載 DockerCon範例](#下載-dockercon範例)
  - [下載 MySQL](#下載-mysql)
    - [docker 指令](#docker-指令)
    - [密碼無法登入的問題](#密碼無法登入的問題)
    - [看一些變數值](#看一些變數值)
    - [建立新用戶](#建立新用戶)
    - [設定 local file 可以上傳](#設定-local-file-可以上傳)
  - [END](#end)

<!-- /TOC -->

---

## basic

### 歷史資訊清除

```{bash}
history -c
history -w
exit
history
```

--

### 重開機

```{bash}
sudo reboot
```

--

### 已經安裝的套件

```{bash}
//列出可安裝的套件(，並計算個數)。
apt list
apt list | wc -l

//列出有安裝的套件，並計算個數。
apt list --installed | wc -l
```

--

### 磁碟使用的初始狀況

-h, --human-readable  print sizes in powers of 1024 (e.g., 1023M)

```{bash}
df -h
```

--

### 權限修改

```{bash}
chmod a+x <filename or folder>

//下面兩個語法等價。
chmod a+rwx <filename or folder>
chmod 777 <filename or folder>
```

--

### 顯示目錄下-檔案-編碼-結尾換行符號

```{bash}
ls
ll
ls -al  <-- 和ll功能相同

  > 可以在後面加路徑，比如 ll /mnt/e/
```

顯示該檔案的編碼與結尾換行符號類型。

```{bash}
file <filename>
```

--

### su 最高權限者

-i, --login: run login shell as the target user; a command may also be specified

```{bash}
//下面兩個效果相同。
sudo su
sudo -i
```

--

### Others

- `whoami`: 顯示使用者名稱。  
- `hostname`: 顯示主機名稱。  
- `ifconfig`: 查詢、設定網路卡與 IP 網域等相關參數。觀察所有的網路介面。用來獲取網路介面配置資訊並對此進行修改。。

--

### 修改 ssh 登入

請看 `ssh_connect.md`

--

### TWCC-port connect

請看 `TWCC-port_connect.md`

---

## mount/umount Disk

注意這邊大部分的操作都需要 sudo su。

### 掛載狀況

- 磁碟使用的初始狀況。  
- -h, --human-readable: print sizes in powers of 1024 (e.g., 1023M)

```{bash}
df -h
```

- 列出所有(掛載中)磁碟

> 利用 blkid 這個指令，它可以列出所有掛載中磁碟的 UUID。  
> blk: 是指 block device，即儲存裝置。

```{bash}
//只會顯示有掛載的
blkid

//顯示所有硬碟
lsblk
```

--

### 格式化、掛載、卸除

先格式化，再掛載~

```{bash}
mkfs -t ext4 /dev/vdb
mount -t ext4 /dev/vdb /datamount
df -h
```

卸除磁碟

```{bash}
umount ext4 /dev/vdb
umount ext4 /datamount  //這兩個都可以。
df -h
```

--

### 設定開機自動掛載

各欄說明：`<file system> <mount point>   <type> <options> <dump> <pass>`  

- file system：磁碟裝置代號或該裝置的 Label。
- mount point：掛載點。
- type：磁碟分割區的檔案系統。
- options：檔案系統參數。
- dump：能否被 dump 備份指令作用。
- pass：是否以 fsck 檢驗磁區。

```{bash}
vi /etc/fstab

//給一個之前用好的範例結果
# <file system> <mount point>   <type> <options> <dump> <pass>  <--我加的註解。
LABEL=cloudimg-rootfs   /        ext4   defaults        0 0  <--原本就有。
LABEL=UEFI      /boot/efi       vfat    defaults        0 0  <--原本就有。
UUID="67370358-c856-468b-b4d9-452bb3741ec3"     /datamount  ext4    defaults        0       0  <--新加的。
```

---

## Docker

紀錄操作的指令。

- 下載 docker
- 加入 docker 帳號到群組
- DockerHub login
- 下載 images-01
  - OS system
    - ubuntu
    - centos
  - website
    - thenetworkchuck/nccoffee:frenchpress，8081
    - DockerCon2020 sample = littlefish0331/hello-world，8080
- 下載 images-02Database
  - mysql
  - Postgress
  - MSSQL
  - mariadb
  - bigobject
  - R+Rstudio
  - python+jupyter notebook

--

### 下載 docker

- [Linux 修改使用者帳號設定 - usermod](https://www.opencli.com/linux/usermod-modify-linux-account)

兩種方法其實是一樣的。

```{bash}
// 這是我從 社群好友 - 紙鈔(money)，那邊學的。
// 從官方網站下載，然後以 shell 執行。
curl -sSL https://get.docker.com/ | sh

// 官方 docker Github 作法
// 先從官方網站下載，儲存檔名為 get-docker.sh
// 再用 sh 執行。
// -o, --output <file> Write to file instead of stdout
curl -fsSL https://get.docker.com -o get-docker.sh
sh get-docker.sh

```

### 加入 docker 帳號到群組

因為 Docker 安裝後，會建立一個 docker 帳號和群組。  
如果沒有把 docker 帳號加入群組，就會北次使用 docker 指令都需要 sudo，  
為了者直接使用 docker 指令，所以要把 docker 加入 ubuntu 群組中。  

- 當使用 "-G" 參數時, usermod 會將帳號從原來加入了的群組退出, 所以在 "-G" 參數前加入 "-a" 參數, 會保留原來的群組設定。
- 記得要重新登入。

```{bash}
sudo usermod -aG docker ubuntu
```

### DockerHub login

```{bash}
docker login
```

### 下載 images-01

- ubuntu

```{bash}
docker pull ubuntu
```

- centos

```{bash}
docker pull centos
```

- thenetworkchuck/nccoffee:frenchpress

```{bash}
// -t, --tty  Allocate a pseudo-TTY。分配偽TTY。
docker run -d -t -p 8081:80 --name nccoffee thenetworkchuck/nccoffee:frenchpress
```

- 下載 DockerCon 範例

```{bash}
docker pull littlefish0331/hello-world
docker run -p 8080:80 --name DockerCon2020 -d littlefish0331/hello-world
```

--

### 下載 images-02Database

#### MSSQL: SQL SERVER

- [Microsoft SQL Server - Docker Hub](https://hub.docker.com/_/microsoft-mssql-server)

```{bash}
// ACCEPT_EULA=Y。confirms your acceptance of the End-User Licensing Agreement.
// userid = 'sa'
// MSSQL_PID，可以選擇 MSSQL 的版本。
// SA_PASSWORD=<your_strong_password>

docker run \
-e "ACCEPT_EULA=Y" \
-e "SA_PASSWORD=P@ssw0rd" \
-p 1433:1433 \
--name mssql -d mcr.microsoft.com/mssql/server:2019-latest

//一行指令
docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=P@ssw0rd" -p 1433:1433 --name mssql -d mcr.microsoft.com/mssql/server:2019-latest
```















### BO_performance_part2

**更改檔案或目錄之擁有者或群組:**

- [Linux 更改檔案擁有者與群組，chown 指令使用教學與範例 - G. T. Wang](https://blog.gtwang.org/linux/linux-chown-command-tutorial/)

```{bash}
chown -R ubuntu /data2/bigobject
```

**建立 postgres, mariadb 的 container:**

```{bash}
docker run --name some-postgres \\
-v /data2/postgres:/var/lib/postgresql \\
-p 3307:3306 -e POSTGRES_PASSWORD=NCHC-COVID19 \\
-e PGDATA=//data/pgdata -dit mariadb

docker run --name some-mariadb \\
-v /data2/mariadb/:/var/lib/mysql \\
-p 3308:3306 -e MYSQL_ROOT_PASSWORD=NCHC-COVID19 -d mariadb
```







#### 下載 MySQL

- [mysql - Docker Hub](https://hub.docker.com/_/mysql?tab=description)
- 會自動建立連動的資料夾。  

```{bash}
docker run --detach \
--name some-mysql \
-v /DBdata/mysql/data:/var/lib/mysql \
-v /DBdata/mysql/conf:/etc/mysql/conf.d \
-p 3306:3306 \
--env MYSQL_ROOT_PASSWORD=DAS@mysql2020 \
mysql:latest

//一行指令
docker run --detach --name some-mysql -v /DBdata/mysql/data:/var/lib/mysql -v /DBdata/mysql/conf:/etc/mysql/conf.d -p 3306:3306 --env MYSQL_ROOT_PASSWORD=DAS@mysql2020 mysql:latest
```

#### 密碼無法登入的問題

這主要是因為 Mysql 版本的問題。密碼加密的方式不同。

- [MySQL 8.0 的新密碼加密 plugin 導致 PHP 連線失敗 - Zeroplex 生活隨筆](https://blog.zeroplex.tw/2019/07/mysql-80-plugin-php.html)
- [連線 MySQL 8.0 時，加密方式不相容的解決方法 | IT人](https://iter01.com/443370.html)
- [Andreas Geisler - Berlin based Full Stack Software Developer](http://www.andreasgeisler.com/blog/fatal-error-uncaught-pdoexception-the-server-requested-authentication-method-unknown-to-the-client-caching_sha2_password/2018/11/)
- [Upgrading to MySQL 8.0 : Default Authentication Plugin Considerations | MySQL Server Blog](https://mysqlserverteam.com/upgrading-to-mysql-8-0-default-authentication-plugin-considerations/)

**Step0:**

之後可以去試試看，在 my.cnf 加上下列資訊。  

```{my.cnf}
[mysqld]
default-authentication-plugin = mysql_native_password
```

或是修改 docker-compose.yml 的 mysql 服務部分，新增一行。

```{docker compose .yml}
command: --default-authentication-plugin=mysql_native_password
```

總之，step0的方法我還沒有嘗試過。

**Step01:**

去 /DBdata/mysql/conf 新增 my.cnf。(嘗試的時候是用 my.conf 也行)。  
新增與修改檔案要用 sudo su 權限。  

```{bash}
docker restart some-mysql
```

**Step02:**

登入 container  
登入 mysql，密碼 DAS@mysql2020

```{bash}
docker exec -it some-mysql bash
mysql -u root -p
```

**Step03:**

指定使用資料庫，更新密碼為空。

```{bash}
use mysql;
select user,authentication_string,host from user;
update user set authentication_string='' where user='root';
flush privileges;
```

**Step04:**

退出mysql，把第一步的skip-grant-tables註釋。再重啟mysql

```{bash}
vi my.cnf
docker restart some-mysql
docker exec -it some-mysql bash
mysql -u root -p
```

**Step05:**

使用原始加密的密碼 + 權限設定

mysql_native_password

```{bash}
use mysql;
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'DAS@mysql2020';
ALTER USER 'root'@'%' IDENTIFIED WITH mysql_native_password BY 'DAS@mysql2020';
GRANT ALL PRIVILEGES ON *.* TO 'root'@'localhost' WITH GRANT OPTION;
```

### 看一些變數值

```{bash}
SHOW VARIABLES LIKE 'lower%';
use mysql;
select user,authentication_string,host from user;
```

### 建立新用戶

但是我還不會給予權限。

```{bash}
CREATE USER 'kvgh'@'%' IDENTIFIED WITH mysql_native_password BY 'kvgh@DB2020';
GRANT ALL PRIVILEGES ON * . * TO 'newuser'@'localhost'; //應該是這個，但是這權限有點太大。
```

### 設定 local file 可以上傳

這樣就可以從程式端上傳資料，也可以用 LOAD 指令上傳local檔案。

```{bash}
SHOW GLOBAL VARIABLES LIKE 'local_infile';
SET GLOBAL local_infile=1;
```

---

## END
