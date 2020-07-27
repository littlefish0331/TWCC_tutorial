# README

公司對員工這麼壞= =，那公司的產品我還不用爆!  
把資源用到大爆炸的那一種XDD~  

記得 VM 剛啟動的時候，建議最好 `sudo reboot` 一下，之前的經驗是有一些檔案好像還處於 lock 狀態。

學習如何在VM上架設各種服務、應用程式、網路設定，以及如何讓不同服務之間溝通。最後打包成果與個體快照:

- Docker
- VM
- program
  - python
  - R, Rstudio
  - JS、CSS、HTML
- DB
  - Mysql
  - BO
  - SQL server
  - MariaDB
- Plumber
- Git
  - Gitbook
  - Gitlab
- FTP
  - FTP Client
  - FTP Server

---

## apt list

```{bash}
<!-- 預設下載的 docker 套件。 -->
apt list | grep ^docker

> docker/bionic 1.5-1build1 amd64
> docker-compose/bionic 1.17.1-2 all
> docker-containerd/bionic 0.2.3+git+docker1.13.1~ds1-1 amd64
> docker-doc/bionic-updates 19.03.6-0ubuntu1~18.04.1 all
> docker-registry/bionic 2.6.2~ds1-1 amd64
> docker-runc/bionic 1.0.0~rc2+git+docker1.13.1~ds1-3 amd64
> docker.io/bionic-updates 19.03.6-0ubuntu1~18.04.1 amd64
> docker2aci/bionic 0.14.0+dfsg-2 amd64
```
