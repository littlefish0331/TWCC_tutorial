# Self Command History

這裡存放自己操作成功，並整理過後的指令。  
基本上這著做就可以到達同樣效果。  

簡單來說就是我的指令記事本啦XD~  
所以這邊都是從其他的 .md 檔複製過來之後，再做一點排版和補充。

---

## 歷史資訊清除

```{bash}
history -c
history -w
exit
history
```

---

## 重開機

```{bash}
sudo reboot
```

---

## Docker

### 下載docker

記得要重新登入

```{bash}
curl -sSL https://get.docker.com/ | sh
sudo usermod -aG docker ubuntu
```

### 連結 docker hub

```{bash}
docker login
```

### 下載 DockerCon範例

```{bash}
docker pull littlefish0331/hello-world
docker images
docker run -p 8080:80 --name DockerCon -d littlefish0331/hello-world
```

---

## 下載 MySQL

- [mysql - Docker Hub](https://hub.docker.com/_/mysql?tab=description)

### docker 指令

會自動建立連動的資料夾。  

```{bash}
docker run --detach \
--name some-mysql \
-v /DBdata/mysql/data:/var/lib/mysql \
-v /DBdata/mysql/conf:/etc/mysql/conf.d \
-p 3306:3306 \
--env MYSQL_ROOT_PASSWORD=DAS@mysql2020 \
mysql:latest

//也可以只打一行
docker run --detach --name some-mysql -v /DBdata/mysql/data:/var/lib/mysql -v /DBdata/mysql/conf:/etc/mysql/conf.d -p 3306:3306 --env MYSQL_ROOT_PASSWORD=DAS@mysql2020 mysql:latest
```

### 密碼無法登入的問題

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

## mount/umount Disk

- [How to Mount and Unmount Filesystem in Linux - TecAdmin](https://tecadmin.net/mount-and-unmount-filesystem-in-linux/)

注意這邊大部分的操作都需要 sudo su。

### 掛載狀況

-h, --human-readable: print sizes in powers of 1024 (e.g., 1023M)

```{bash}
df -h
```

利用 blkid 這個指令，它可以列出所有磁碟的 UUID。  
blk: 是指 block device，即儲存裝置。

```{bash}
blkid
```

### 掛載與卸除

先格式化，再掛載~

```{bash}
mkfs -t ext4 /dev/vdb
mount -t ext4 /dev/vdb /data2
df -h
```

卸除磁碟

```{bash}
umount ext4 /dev/vdb 
umount ext4 /data2  //這兩個都可以。
df -h
```

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

//給一個之前用的範例
UUID="1cfa6a6c-09ef-4e20-9893-45d0bdd49e03"     /data2  ext4    defaults        0       0
```

---

## END
