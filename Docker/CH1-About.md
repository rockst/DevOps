# About

> 可以把 Docker 容器當作一種沙盒 Sandbox，每個容器執行一個應用，彼此隔離，彼此可以溝通。容器開啟和停止都十分迅速

>		Build, Ship and Run Any App, Anywhere

>	https://github.com/docker/docker

* 基於 GO 語言食現的雲端開源專案
* Docker 引擎基礎是 Linux Containers - LXS
* 2013 dotCloud 改名 Docker, Inc.
* Redhat RHEL 6.5/CentOS 6.5/Ubuntu 14.04
* PasS/Azure/Windows Server
* AWS EC2 Container

## 優點

* 快速部署：使用映像檔來快速建構一套標準系統。
* 高效率的資源利用：不需額外的虛擬話管理工具，它是內核層級的虛擬化。
* 任意平台
* 簡單的更新：Dockerfile

## 與傳統虛擬話的差別

![](http://image.slidesharecdn.com/dockerfromscratch-160208083101/95/docker-from-scratch-9-638.jpg?cb=1454920342)

* 傳統是在硬體層虛擬化，Docker則是在作業系統層

# Install

* Image 映像檔
* Container 容器
* Repository 倉庫

## Image

* 一個 Image 只能一個應用
	* 一個 Ubuntu Image
	* 一個 Apache Image

## Container

* 一個 Sandbox
* 簡易版的 Linux

## Repository

* Docker 存放 Image 的場所
* 每個 Repository 存放同類的 Image
	* 使用不同 tag 分開
* Public: 
	* [Docker Hub](https://registry.hub.docker.com)
	* [Docker Pool](http://dockerpool.com)
* Private

## Install

### Ubuntu 14.04

	sudo apt-get update
	sudo apt-get install -y docker.io
	sudo ln -sf /bin/docker.io /usr/local/bin/docker
	sudo sed -i '$acomplete -F _docker docker' /etc/bash_completion.d/docker.io
	
	OR
	
	sudo apt-get install apt-transport-https
	sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 36A1D7869245C8950F966E92D8576A8BA88D21E9
	sudo bash -C "echo deb https://get.docker.io/ubuntu docker main > /etc/apt/sources.list.d/docker.list"
	sudo apt-get update
	sudo apt-get install -y lxc-docker
	
	更新
	
	sudo apt-get update -u lxc-docker
	
	  
### Mac OS

* Mac 由於是一個封閉的 Linux 所以安裝上需要透過一個 Tool: boot2docker 來產生 VM 進行安裝
* [下載 boot2docker](https://github.com/boot2docker/osx-installer/releases)
* [安裝 By Rain](http://ephrain.pixnet.net/blog/post/59556208)
* [安裝 By Josh](https://joshhu.gitbooks.io/docker_theory_install/content/DockerBible/mac_osboot2docker.html)

>	boot2doocker 指令

	boot2docker init
	boot2docker start -- 開啟
	boot2docker stop -- 停止

> boot2docker 連線
	
	boot2docker ssh

## Image

### 取得 Image

	docker pull ubuntu
	docker pull ubuntu:14.04 - 加版號
	docker pull ubuntu:latest - 最新板
	
> 設定 Image Tag 為 xxx
	
	docker tag xxx ubuntu:latest
	
### 瀏覽所有 Images
	
	docker images
	
> 查尋某個 image 的資訊 (JSON格式)

	docker inspect image_id
	docker inspect -f {{".RootFS.Layers"}} image_id
	
### 在公開的 Pool 搜尋某個 image
	
	docker search mysql
		--automated=false // 顯示自動建立的 image
		--stars=0 指定幾顆星以上

### 刪除某個 image

	docker rmi tag_name or image_id
	docker rmi -f xxx - 強制刪除 
	
### 建立 image

> 設定一個 image 的變動

	docker run -ti ubuntu /bin/bash
	touck test
	exit
	(記住容器的ID）:87b98cf92493
	root@87b98cf92493:/# exit

> 產生一個 image

	docker commit -m 'Commit message' -a 'Author name' 容器ID 新的ImageID

### 儲存和載入 image

	docker save -o output_filename.tar REPOSITORY:TAG
	docker load -i input_filename.tar
	
### 上傳 image 到 Docker Hub

* [Docker Hub](https://dockerhub.com) 註冊一個帳號: rockstlin
* 建立一個 REPOSITORY ＝> rockstlin/test
* 回到本端機的 Docker
	* docker login 登入
	* Tag 你要 push 的 image
		* docker tag repository:tag rockstlin/test(dockerhub 帳號/dockerhub repostory)
	* docker push rockstlin/test
	
	
	


	
