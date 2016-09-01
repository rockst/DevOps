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