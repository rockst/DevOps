
# 刪除所有已經無用的 Docker 資源

## 以下命令可以列出所有 Untag 的容器映像:

    docker images --filter "dangling=true"

只顯示 Image ID

    docker images --filter "dangling=true" -q

## 快速移除所有無用的容器映像

    docker rmi $(docker images -f "dangling=true" -q)

OR

    docker image prune

## 移除所有沒用到的容器映像

    docker image prune -a

## 移除所有沒用到的 Docker 物件

+ stopped containers
+ dangling networks
+ dangling images
+ dangling build cache

    docker system prune -a
