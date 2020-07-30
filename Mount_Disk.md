# Mount Disk

其實就和在 windows 系統一樣，要新增硬碟，也就是掛上去之前，都是要初始化的。  
然後 linux 的硬碟格式可能和我們熟知的不太一樣。

- windows 推薦 NTFS
- Linux 推薦 ext4

---

## 硬碟 - 掛載狀況 + 格式化 + 掛載 + 卸除

- [用 Linux blkid 命令查找塊設備詳情 - 每日頭條](https://kknews.cc/zh-tw/tech/3m988oo.html)
- [鳥哥的 Linux 私房菜 -- 第七章、Linux 磁碟與檔案系統管理](http://linux.vbird.org/linux_basic/0230filesystem.php#lsblk)
- [替 Linux 新增硬碟（磁碟分割、格式化與掛載） - G. T. Wang](https://blog.gtwang.org/linux/linux-add-format-mount-harddisk/)
- [mount - 掛載儲存裝置指令 | 凍仁的筆記](http://note.drx.tw/2008/02/ubuntu-mount.html)
- [Linux 檔案系統掛載（mount）使用教學與範例 - G. T. Wang](https://blog.gtwang.org/linux/linux-mount/)

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

---

## 分割硬碟

由於 MBR 分割表不支援超過 2TB 的磁碟，如果您的硬碟大小超過 2TB，就無法使用 fdisk 分割硬碟，請改用 parted 以 GPT 的方式分割

- [Linux 的 Parted 指令教學：建立、變更與修復磁碟分割區 - G. T. Wang](https://blog.gtwang.org/linux/parted-command-to-create-resize-rescue-linux-disk-partitions/)

---
