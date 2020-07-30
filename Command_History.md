# Command History

## 歷史資訊清除

```{bash}
history -c
history -w
exit
history
```

## 重開機

```{bash}
sudo reboot
```

## 下載docker

記得要重新登入

```{bash}
curl -sSL https://get.docker.com/ | sh
sudo usermod -aG docker ubuntu
```

## 連結 docker hub

```{bash}
docker login
```

---

## 下載 DockerCon範例

```{bash}
docker pull littlefish0331/hello-world
docker images
docker ps -a
docker run -p 8080:80 --name DockerCon -d littlefish0331/hello-world
```

---

## 下載 MySQL

會自動建立連動的資料夾。  
[mysql - Docker Hub](https://hub.docker.com/_/mysql?tab=description)

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

**Step01:**

去 /DBdata/mysql/conf 新增 my.cnf。(嘗試的時候是用 my.conf 也行)。  
新增與修改檔案要用 sudo su 權限。

```{bash}
docker restart some-mysql
```

**Step02:**

登入 container  
登入mysql，密碼DAS@mysql2020

```{bash}
docker exec -it some-mysql bash
mysql -u root -p
```

**Step03:**

指定使用資料庫，  
更新為空。

```{bash}
use mysql;
select user,authentication_string,host from user;
update user set authentication_string='' where user='root';
flush privileges;
```

**Step04:**

退出mysql，把第一步的skip-grant-tables註釋。再重啟mysql

```{bash}
vi my.conf
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

但是我還不會給予權限

```{bash}
CREATE USER 'kvgh'@'%' IDENTIFIED WITH mysql_native_password BY 'kvgh@DB2020';
GRANT ALL PRIVILEGES ON * . * TO 'newuser'@'localhost'; //應該是這個但是這權限有點太大。
```

### 設定 local file 可以上傳，也就是可以用 LOAD 指令

```{bash}
SHOW GLOBAL VARIABLES LIKE 'local_infile';
SET GLOBAL local_infile=1;
```

---

## mount 硬碟

掛載狀況。  
-h, --human-readable: print sizes in powers of 1024 (e.g., 1023M)

```{bash}
df -h
```

利用 blkid 這個指令，它可以列出所有磁碟的 UUID。  
blk: 是指 block device，即儲存裝置。

```{bash}
blkid
```

先格式化，再掛載~

```{bash}
mkfs -t ext4 /dev/vdb
mount -t ext4 /dev/vdb /data2
df -h
```
