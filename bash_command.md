# bash_command

`whoami`: 顯示使用者名稱。  
`hostname`: 顯示主機名稱。  
`ifconfig`: 查詢、設定網路卡與 IP 網域等相關參數。觀察所有的網路介面。用來獲取網路介面配置資訊並對此進行修改。。

---

## 最高權限者

-i, --login: run login shell as the target user; a command may also be specified

```{bash}
//下面兩個效果相同。
sudo su
sudo -i
```

---

## Linux 系統支援語系

- Linux 系統預設支援的語系資料：這與 /etc/locale.conf 有關
- 終端介面 (bash) 的語系： 這與 LANG, LC_ALL 這幾個變數有關

---

## 顯示目錄下的檔案

```{bash}
ls
ll
ls -al  <-- 和ll功能相同

  > 可以在後面加路徑，比如 ll /mnt/e/
```

顯示該檔案的編碼與結尾。

```{bash}
file <filename>
```

---

## 資料夾權限

- [鳥哥的 Linux 私房菜 -- 第五章、Linux 的檔案權限與目錄配置](http://linux.vbird.org/linux_basic/0210filepermission.php)

其實就是把 3*3*3=9 的作法，作一些符號上的替換。

```{bash}
chomod a+x *。  
```
