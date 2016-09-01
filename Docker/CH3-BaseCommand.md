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