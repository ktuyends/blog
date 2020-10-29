---
title: "Install Software in Ubuntu"
slug: install-software-in-ubuntu
date: 2016-03-10
categories:
- Tutorial
tags:
- Tutorial
showTags: false
thumbnailImagePosition: "left"
thumbnailImage: /post/03-tutorial/img/cover/ubuntu-software.png
clearReading: true
metaAlignment: center
comments: true
description: "Tutorial"
summary: >
  Trong post này, mình tổng hợp lại một số phần mềm cơ bản nên cài cho Ubuntu và một số phần mềm khác như MySQL, Rstudio, Anaconda để làm việc với Data...
---

Trong post này, mình tổng hợp lại một số phần mềm cơ bản nên cài cho Ubuntu và một số phần mềm khác như MySQL, Rstudio, Anaconda để làm việc với Data.

#### 1. Một số phần mềm cơ bản:

- Phân vùng ổ cứng: `sudo apt install gparted`
- Giải nén: `sudo apt install p7zip-full p7zip-rar`
- Media codecs: `sudo apt install ubuntu-restricted-extras`
- Text editor: Sublime text, Visual Studio Code
- Nghe nhạc: Spotify, Sayonaram, VLC

```shell
$ sudo apt-add-repository ppa:lucioc/sayonara
$ sudo apt-get update
$ sudo apt-get install sayonara
```

- Snap:

```shell
$ sudo apt update
$ sudo apt-get install snapd
$ snap find <search_text>
$ sudo snap install <package>
$ snap list
$ sudo snap remove <package>`
```

- Đọc file PDF: Foxit Reader
- Đọc file Epub: Calibre
- Ghi chú: Typora

```shell
$ wget -qO - https://typora.io/linux/public-key.asc | sudo apt-key add -
$ sudo add-apt-repository 'deb https://typora.io/linux ./'
$ sudo apt-get update
$ sudo apt-get install typora
```

- Paint: Krita, Pinta

```shell
$ sudo add-apt-repository ppa:kritalime/ppa
$ sudo apt-get update
$ sudo apt-get install krita
```

- Image Editors: GIMP, Inkscape

```shell
$ sudo add-apt-repository ppa:otto-kesselgulasch/gimp
$ sudo apt-get update
$ sudo apt-get install gimp
```

- Photography: DigiKam, Darktable

- Video editors: Kdenlive, Shotcut

```shell
$ sudo snap install shotcut --classic
```

- Image and video converter: Xnconvert, Handbrake

```shell
$ wget https://download.xnview.com/XnConvert-linux-x64.deb
$ sudo dpkg -i XnConvert-linux-x64.deb
```

- Screenshot and screen recording tools: Shutter, Kazam

```shell
$ sudo add-apt-repository ppa:linuxuprising/shutter
$ sudo apt-get update
$ sudo apt install shutter
$ sudo apt install gnome-web-photo
```

- Latex

```shell
sudo apt-get install texlive-full
```

- Office: https://www.office.com/, OnlyOffice

- Firefox Extension: Flash Video Download
- Chrome Extension: AdGuard AdBlocker
- Download tool: uget, aria2

```shell
$ sudo apt install uget aria2
```

- Dọn rác: Bleachbit
- Một số phần mềm khác: Mendeley, Teamview, Dropbox, Skype

#### 2. Install Hugo & Git

- Cài đặt Git:

```shell
$ sudo apt-get update
$ sudo apt-get install git
$ git --version
```

- Cài đặt Hugo: Lên Github, tải file `.deb` về cài đặt như bình thường.

- Cài đặt Nodejs:

```shell
$ curl -sL https://deb.nodesource.com/setup_13.x | sudo -E bash -
$ sudo apt-get install -y nodejs
```

- Cài đặt Git GUI: Gitkraken, Pycharm

```shell
$ sudo snap install pycharm-community --classic
```

#### 3. Install R & Rstudio

- Cài đặt R:

```shell
$ sudo apt install apt-transport-https software-properties-common
$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E298A3A825C0D65DFD57CBB651716619E084DAB9
$ sudo add-apt-repository 'deb https://cloud.r-project.org/bin/linux/ubuntu disco-cran35/'

$ sudo apt update
$ sudo apt install gdebi libxml2-dev libssl-dev libcurl4-openssl-dev libopenblas-dev r-base r-base-dev
```

- Cài đặt Rstudio:

```shell
$ cd ~/Downloads
$ wget https://download1.rstudio.org/desktop/bionic/amd64/rstudio-1.2.5001-amd64.deb
$ sudo gdebi rstudio-1.2.5001-amd64.deb
```

- Cài đặt JAGS:

```shell
$ sudo apt-get install jags
```

#### 4. Install MySQL

```shell
$ sudo apt-get install mysql-server
$ sudo apt install mysql-workbench
```

#### 5. Install Anaconda

Đầu tiên, các bạn vào trang Web của Anaconda và tải file cài đặt Anaconda về. Sau đó chạy lệnh sau để cài đặt:

```shell
$ bash filename.sh
```

- Tạo Anaconda Navigator Icon

```shell
$ sudo nano /usr/share/applications/Anaconda.desktop
```

Điền nội dung sau vào trong file:

```shell
[Desktop Entry]
Version=1.0
Type=Application
Name=Anaconda
GenericName=Anaconda
Exec=bash -c 'export PATH="/home/ktuyends/anaconda3/bin:$PATH" && /home/ktuyends/anaconda3/bin/anaconda-navigator'
Icon=/home/ktuyends/anaconda3/lib/python3.7/site-packages/anaconda_navigator/static/images/anaconda-icon-256x256.png
Terminal=false
StartupNotify=true
MimeType=text/x-python;
```

Cuối cùng sử dụng các phím tắt sau để hoàn tất: `Ctrl + O` -> `Enter` -> `Ctrl + X`.

---