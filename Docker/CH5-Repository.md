# Repository

## Docker Hub

> [Docker Hub](https://hub.docker.com/)

	docker login

## Docker Pool

> [Docker Pool](http://dockerpool.com)

## 私有

> 使用 registry image 架設 Private Repository

	docker run -d -p 5000:5000 registry
	docker run -d -p 5000:5000 -v /opt/data/registry:/tmp/registry registry:latest
	
	docker tag REPOSTORY:TAG 10.0.2.2:5000/test
	docker push 10.0.2.2:5000/test
	
	curl http://10.0.2.2:5000/v1/search
	
	docker pull 10.0.2.2:5000/test