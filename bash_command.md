# bash_command

## apt

**list:**

列出所有的套件。  
list packages based on package names

```{bash}
apt list
apt list --installed  //列出所有安裝的套件。
```

靈活運用

```{bash}
apt list | wc -l
apt list --installed | wc -l
apt list | grep ^docker  //dcoker 開頭的套件。
```

---

## Others

- `whoami`: 顯示使用者名稱。  
- `hostname`: 顯示主機名稱。  
- `ifconfig`: 查詢、設定網路卡與 IP 網域等相關參數。觀察所有的網路介面。用來獲取網路介面配置資訊並對此進行修改。。

---

## su 最高權限者

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

---

## View History

- ubuntu帳號下的指令紀錄放在 /home/ubuntu/.bash_history 中。
- echo $HISTFILE，可以得到上面的路徑。操作歷史紀錄，儲存的檔案位置。(操作歷史紀錄檔)(.bash_history)。
- echo $HISTFILESIZE，操作歷史紀錄檔，最多儲存幾筆。
- echo $HISTSIZE，history 最多列出幾筆(在記憶體中存放的筆數)。

更多設定與操作請參考: [XYZ的筆記本: Linux Bash 刪除 history 指令操作歷史紀錄](https://xyz.cinc.biz/2017/08/linux-bash-history-clear.html)

### window

關於 windows 的 cmd 歷史紀錄，  
請按 F7，或是指令 `doskey /history`

---

## df

- -h: 列出硬碟使用的初始狀況。

## END
