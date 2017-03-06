---
layout: post
title: VPS 常用命令
categories: [VPS]
tags : [ubuntu linux]
---


## 登录远程主机

```
sudo ssh spaling@107.170.231.223 -p 21
```

**选项**

    -p  指定远程主机的端口. 可以在配置文件中对每个主机单独设定这个参数.

## 压缩

```
sudo zip -qr thus.zip /home/wwwroot/thus
```

**选项**

    -q：不显示指令执行过程；
    -r：递归处理，将指定目录下的所有文件和子目录一并处理；

将/home/wwwroot/thus目录压缩成thus.zip

**选项**

    -q  安静模式，在压缩的时候不显示指令的执行过程
    -r  将指定的目录下的所有子目录以及文件一起处理

## 解压
```
sudo unzip thus.zip
```
```
sudo unzip -d /home/wwwroot/ thus.zip
```

**选项**

    -d<目录>：指定文件解压缩后所要存储的目录；

将thus.zip解压到当前目录

## 移动

```
sudo mv thus.zip /home/wwwroot/
```
将当前目录下的thus.zip压缩文件移动到/home/wwwroot/目录下

## 重命名

```
sudo mv /home/wwwroot/thus /home/wwwroot/thusin
```
将thus重命名为thusin

## 删除

```
sudo rm -rf /home/wwwroot/thus
```
递归删除/home/wwwroot/thus目录及其下的文件

**选项**

    -f：强制删除文件或目录；
    -r或-R：递归处理，将指定目录下的所有文件与子目录一并处理；
    --preserve-root：不对根目录进行递归操作；
    -v：显示指令的详细执行过程。

## 权限

### 1.更改文件所有者

```
sudo chown -R www:www /home/wwwroot/thus
```
更改整个文件夹的拥有者和用户组为www

### 2.更改文件的权限

```
sudo chmod 777 /home/wwwroot/thus
```

更改读取、写入、执行权限

## 显示每个文件和目录的磁盘使用空间

```
du -h --max-depth=1 thus
```

**选项**

    -a或-all 显示目录中个别文件的大小。
    -b或-bytes 显示目录或文件大小时，以byte为单位。
    -c或--total 除了显示个别目录或文件的大小外，同时也显示所有目录或文件的总和。
    -k或--kilobytes 以KB(1024bytes)为单位输出。
    -m或--megabytes 以MB为单位输出。
    -s或--summarize 仅显示总计，只列出最后加总的值。
    -h或--human-readable 以K，M，G为单位，提高信息的可读性。
    -S或--separate-dirs 显示个别目录的大小时，并不含其子目录的大小。
    -X<文件>或--exclude-from=<文件> 在<文件>指定目录或文件。
    --exclude=<目录或文件> 略过指定的目录或文件。
    -H或--si 与-h参数相同，但是K，M，G是以1000为换算单位。
    --max-depth=n 只输出命令行参数的小于等于第 n 层的目录的总计。 --max-depth=0的作用同于-s选项。(fileutils-4.0的新选项)