# Container

>		Container 是 Image 一個執行的實例（Instance），它帶有額外的可寫層

## 建立

>	使用 create 產生容器後，是處於停止的狀態

	docker create -it REPOISTORY:TAG
	
## 查看 Container 執行（已停止）

	docker ps -a
	
## run container 的操作

	docker run ubuntu /bin/echo 'hello world'
	
*	檢查本機是否有 ubuntu image 沒有會從 public pool 下載
*	利用 ubuntu image 建立一個 container
*	分配一個檔案系統，在唯讀的 image 外掛上一個可讀寫層
*	從 HOST 的喬接介面 docker0 中橋接一個虛擬介面到 Container 中
*	從 172.17.0.0/24 賦予一個 IP 給 Container
*	執行應用程式 /bin/echo 'hello world'
*	停止 Container

	docker run -ti ubnutu:latest /bin/bash
	-t docker 分配一個虛擬終端 pseudi-tty 榜定到 container 的標準輸入上
	-i 持續將標準輸入打開
	
## 背景下執行

	docker run -d ubuntu:latest /bin/sh -c "while true; do echo hello; sleep 1; done"
	
> 查看執行中 Container

	docker ps
	
> 查看 Container logs

	docker logs CONTAINER_ID

> 進入背景中的 Container

	docker attach CONTAINER_ID
	
## 停止

	docker stop CONTAINER_ID
	
## 啟動

	docker start CONTAINER_ID （已停止）
	docker restart CONTAINER_ID （執行中）
	
## 刪除

	docker rm CONTAINER_ID
	
## 匯出

	docker export CONTAINER_ID > file_name.tar
	
	關於 Save 與 Export 對 Image 之間的差異
	https://ithelp.ithome.com.tw/articles/10193804
	
## 匯入

	docker import file_name
	cat file_name.tar | docker import - test/ubuntu:v1.0
	
## Commit 到 image
	docker commit -m 'message' -a 'Auther' CONTAINER_ID IMAGE_NAME:TAG
	

