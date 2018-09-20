# 第一章 认识

主要目标：通过对应用的组件的封装、分发、部署、运行等生命周期的管理，达到应用级别的一次封装，到处运行。

为什么使用docker:

​	1、环境隔离：通过cgropus和namespace进行实现资源隔离，实现一台机器运行多个容器互不影响。

​	2、更快速的交付部署：使用docker，开发人员可以利用奖项快速构建一套标准的研发环境；开发完成后，测试和运维人员可以直接通过使用相同的环境来部署代码。docker 可以快速创建和删除容器，实现快速迭代，大量节约开发、测试、部署的时间。并且，各个不走都有明确的配置和操作，整个过程全程公司内文档说明，使团队更容易理解应用创建和工作的过程。

​	3、更高效的资源利用：docker容器的运行不需要额外的虚拟换管理程序的支持，他是内核级的虚拟化，可以实现更高的性能，同时对资源的额外需求很低。

​	4、更易迁移扩展：docker容器几乎可以再任意的平台上运行，包括乌力吉、虚拟机、私有云、公有云、个人电脑、服务器等，这种兼容性让用户可以再不同平台之间轻松的迁移应用。

​	5、更简单的更新管理：使用dockerfile，只需要小小的配置修改，就可以替代以往的大量的更新工作，并且所有修改都是以增量的方式进行分发和更新，从而实现自动化和高校的容器管理。 

虚拟化与docker：虚拟化是一种资源管理技术，是将计算机的各种实体资源，如服务器、网络、内存及存储等，予以抽象、转换后呈现出来，打破实体结构件的不可切割的障碍，使用户可以比原本的配置更好的方式来应用这些资源。浙西资源的虚拟机部分是不受现有资源的架设方式、低于或物理配置所显示。一般所指的虚拟化资源包括计算能力和数据存储。

# 第二章 核心概念

1、镜像

docker 镜像就是一个只读的模版。

例如：一个镜像可以包含一个完整的centos操作系统环境，里面仅安装了apach或用户需要的其他应用程序。

镜像可以用来创建docker容器

2、容器

容器是从镜像创建的运行实例。他可以被启动开始，停止，删除。每个容器都是相互隔离的，保证安全的平台。

# 第三章 镜像的操作

1、获取镜像

```
docker pull <域名>//
说明： 镜像是docker运行容器的前提
```

2、查看进项李彪

```
docker images
说明：使用docker images命令可以列出本地主机上已有的镜像
```

3、查看镜像信息

```
docker inspect
说明：docker inspect命令返回的是一个json的格式消息，日过我们只要其中的意向内容时，可以通过-f参数来指定
```

4、查找镜像

```
docker search
说明：使用docker search命令可以搜索远端仓库中共享的镜像，默认搜索docker hub 官方仓库中的镜像
```

5、删除镜像

```
docker rmi:
说明：使用docker rmi 命令可以删除镜像，其中image可以为标签或ID
```

6、创建镜像

```
docker commit
参数说明：
-a，--author: 作者信息
-m，--message: 提交消息
-p，--pause=true：提交时暂停容器运行
```

7、迁出镜像

```
docker save -o tar
参数说明：
	-o:设置存储压缩后的文件名称
```

8、载入镜像

```
docker load --input tar 或docker load < tar
说明：使用docker load命令可以载入进项，其中image可以为标签或ID。这将导入及镜像及相关的原数据信息（包括标签等），可以使用docker images命令进行查看，
```

9、上传镜像

```
docker push <域名>//
说明：可以使用docker push命令上传镜像到仓库，默认上传到dockerhub官方仓库
```

# 第四章 容器的基本操作

1、创建容器

```
docker create 
eq:docker create --name test_create -ti ubuntu
```

创建并启动容器

```
docker run
	eq: docker run ubuntu /bin/echo “Hello World”
 docker run -ti -d --name test_network ubuntu bash
 docker exec -ti test_network bash
 // 让docker容器运行在后台以守护态（daemonized）形式运行，可以通过添加-d参数来实现
 docker run –d ubuntu /bin/sh -c "while true;do echo hello world;sleep 1;done”
 //查看日志：docker logs
 docker logs ed95736a20e9
```

2、终止容器

```
docker stop
//查看终止的容器
docker ps -a
//查看运行的容器
docker ps
//重新启动容器
docker start
```

3、进入容器

```
docker exec
eq: docker exec -i -t 630c4d2291e3 bash
```

4、删除容器

```
docker rm <name>
eq: docker ps -a 
	docker rm test2
	//如果正在运行该容器，则先删除
	docker stop test2
```

5、导入和导出容器

```
docker export
eq: docker export test_id > test.tar
docker import
eq: cat export.tar | docker import -liming/testingport:latest
```

