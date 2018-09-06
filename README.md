## Installation


### 网易云

#### 网易云音乐1.0.0(该版本较为好安装)//废弃，解决了1.1.0
```
# 下载地址
http://s1.music.126.net/download/pc/netease-cloud-music_1.0.0_amd64_ubuntu16.04.deb

# 将网易云音乐文件放到家目录

# 先创建软件包目录
mkdir -p netease-cloud-music/DEBIAN
# 用dpkg解压
dpkg-deb -x netease-cloud-music_1.0.0_amd64_ubuntu16.04.deb netease-cloud-music/
dpkg-deb -e netease-cloud-music_1.0.0_amd64_ubuntu16.04.deb netease-cloud-music/DEBIAN

然后用文本编辑器打开netease-cloud-music/DEBIAN/control，找到Depends行，把libqt5libqgtk2修改为qt5-style-plugins
\\删除libqt5libqgtk2
\\删除libfontconfig1 (>= 2.11.94)中的(>= 2.11.94)

然后重新打包：
# 重新打包
dpkg-deb -b netease-cloud-music

#最后重新安装:
sudo dpkg -i  netease-cloud-music.deb

# 一般情况下会提示安装失败，缺失依赖，所以先解决依赖问题
sudo apt install -f

# 接着重复第一步安装搜狗输入法的命令
# 一般 deb 包都是如此安装的，如果失败就去解决依赖问题

#1080P的屏幕应该正常了，如果是3k屏幕字体会过小
sudo gedit /usr/share/applications/netease-cloud-music.desktop

# 修改 Exec 这一行内容：
Exec=sudo netease-cloud-music %U --force-device-scale-factor=2
```

#### 网易云音乐1.1.0
```
# 安装:
sudo dpkg -i  netease-cloud-music_1.1.0_amd64_ubuntu.deb 

# 修改桌面文件
sudo gedit /usr/share/applications/netease-cloud-music.desktop

# 对应行改为
Exec=sh -c "unset SESSION_MANAGER && netease-cloud-music %U --force-device-scale-factor=2"
```

### ss
https://www.k-xzy.xyz/archives/6486

sudo dpkg -i QtShadowsocks_2.1.0-0.1.1-Linux.deb
sudo dpkg -i shadowsocks-qt5_3.0.1-0.1.1-Linux.deb

### gitkraken
ubuntu利用deb包安装完gitkraken后，点击快捷方式无法启动的解决方法：
##1. whereis gitkraken     //查询gitkraken的安装路径，一般是/usr/bin,或者/usr/share

##2. 在安装目录下手动执行  ./gitkraken，可能出现如下的报错信息：


 Gtk-Message: 13:30:22.860: Failed to load module "canberra-gtk-module"
 Node started time: 1529731823072
 libgnome-keyring.so.0: æ æ³æå¼å
 ±äº«å¯¹è±¡æä»¶: æ²¡æé£ä¸ªæä»¶æç®å½
 Error: libgnome-keyring.so.0: æ æ³æå¼å
 ±äº«å¯¹è±¡æä»¶: æ²¡æé£ä¸ªæä»¶æç®å½
 at process.module.(anonymous function) [as dlopen] (ELECTRON_ASAR.js:172:20)
 at Object.Module._extensions..node (module.js:598:18)
 at Object.module.(anonymous function) [as .node] (ELECTRON_ASAR.js:186:18)
 at Module.load (module.js:503:32)
 at tryModuleLoad (module.js:466:12)
 at Function.Module._load (module.js:458:3)
 at Module.require (module.js:513:17)
 at require (internal/module.js:11:18)
 at Object.<anonymous>(/usr/share/gitkraken/resources/app.asar/node_modules/keytar/lib/keytar.js:4:12)
 at Object.<anonymous>(/usr/share/gitkraken/resources/app.asar/node_modules/keytar/lib/keytar.js:58:4)
#2.1 Failed to load module "canberra-gtk-module"的解决方法：

      sudo apt-get install libcanberra-gtk-module

#2.2  Error: libgnome-keyring.so.0解决方法:

     sudo apt-get install libgnome-keyring-common libgnome-keyring-dev 




