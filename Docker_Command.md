# Docker Command

簡單記錄使用過的 docker 指令，有點類似 cheet sheet。  

- docker version: docker 的 version。  

- docker run: Run a command in a new container
  - docker run [OPTIONS] IMAGE [COMMAND] [ARG...]
  - -i, --interactive                    Keep STDIN open even if not attached
  - -d, --detach                         Run container in background and print container ID
  - -t, --tty                            Allocate a pseudo-TTY

- docker pull: Pull an image or a repository from a registry
  - Usage:  docker pull [OPTIONS] NAME[:TAG|@DIGEST]
  - -q, --quiet                   Suppress verbose output

- docker load: Load an image from a tar archive or STDIN
  - Usage:  docker load [OPTIONS]
  - -i, --input string   Read from tar archive file, instead of STDIN
  - -q, --quiet          Suppress the load output

- docker import: Import the contents from a tarball to create a filesystem image
  - Usage:  docker import [OPTIONS] file|URL|- [REPOSITORY[:TAG]

- docker build: Build an image from a Dockerfile
  - Usage:  docker build [OPTIONS] PATH | URL | -

- docker images: List images
  - Usage:  docker images [OPTIONS] [REPOSITORY[:TAG]
  - -a, --all             Show all images (default hides intermediate images)
  - -q, --quiet           Only show numeric IDs

- docker ps: List containers
  - Usage:  docker ps [OPTIONS]
  - -a, --all             Show all containers (default shows just running)
  - -q, --quiet           Only display numeric IDs

- docker start: Start one or more stopped containers
  - Usage:  docker start [OPTIONS] CONTAINER [CONTAINER...]
  - example: docker start <container name or container ID>

- docker stop: Stop one or more running containers
  - Usage:  docker stop [OPTIONS] CONTAINER [CONTAINER...]
  - example: docker stop <container name or container ID>

- docker rm: Remove one or more containers
  - Usage:  docker rm [OPTIONS] CONTAINER [CONTAINER...]
  - example: docker rm <container name or container ID>

- docker exec: Run a command in a running container
  - Usage:  docker exec [OPTIONS] CONTAINER COMMAND [ARG...]
  - example: docker exec <container name or container ID>
  - -i, --interactive          Keep STDIN open even if not attached
  - -t, --tty                  Allocate a pseudo-TTY
  - -w, --workdir string       Working directory inside the container
  - bash|sh: 用甚麼 command mode 去進入操作 container。

- docker logs: Fetch the logs of a container
  - Usage:  docker logs [OPTIONS] CONTAINER
  - example: docker logs <container name or container ID>
  - -f, --follow         Follow log output

- docker rmi: Remove one or more images
  - Usage:  docker rmi [OPTIONS] IMAGE [IMAGE...]

- docker export: Export a container's filesystem as a tar archive
  - Usage:  docker export [OPTIONS] CONTAINER

---

## 參考資料 - cheatsheet

更多請去 cheatsheet/ 資料夾觀看。

- [wsargent/docker-cheat-sheet: Docker Cheat Sheet](https://github.com/wsargent/docker-cheat-sheet)
- [docker_cheatsheet_r3v2.pdf](https://design.jboss.org/redhatdeveloper/marketing/docker_cheatsheet/cheatsheet/images/docker_cheatsheet_r3v2.pdf): 裡面還有 Dockerfile 的指令。
- [The Ultimate Docker Cheat Sheet | dockerlabs](http://dockerlabs.collabnix.com/docker/cheatsheet/)

---

## windows Docker 群組權限

使用 windows 系統下的 Docker 時，  
會預設建立一個 docker group，所以要把使用者加到那個群組。

- [針對 Windows 上的 Docker 用戶端錯誤進行疑難排解 - Visual Studio | Microsoft Docs](https://docs.microsoft.com/zh-tw/visualstudio/containers/troubleshooting-docker-errors?view=vs-2019)

windows + x > 電腦管理 > 本機使用者和群組 > 群組 > docker-users。  
到這裡面做設定。
