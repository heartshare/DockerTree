# DockerTree
Docker容器技术研究

<pre>
Docker
     Docker是基于Go语言实现的云开源项目，诞生于2013年。

     Docker引擎的基础是Linux容器（Linux Containers， LXC）技术。

     Linux容器：
          容器有效的将由单个操作系统管理的资源划分到孤立的组中，以便更好的在孤立的组之间平衡有冲突的资源使用需求。与虚拟化相比，
          这样既不需要指令级模拟，也不需要即时编译，容器可以在核心CPU本地运行指令，而不需要任何专门的解释机制，
     从Linux容器到Docker
          在LXC的基础上，Docker进一步优化了容器的使用体验，Docker提供了各种容器管理工具（如分发，版本，移植）让用户无需关注底层的实现，可以简单明了地管理和使用容器，用户操作Docker容器就像操作一个轻量级的虚拟机那样简单。
</pre>

<pre>
Docker容器虚拟化的好处
    1）高效的构建应用
       例如用户试图基于最常见的LAMP(Linux, Apache, Mysql, PHP)组合来运维一个网站，按照传统的做法，首先需要安装Apache, Mysql, PHP以及他们各自运行锁依赖的环境，之后分别进行配置，经过大量的操作后，还需要进行功能测试，看是否工作正常，如果不正常，则意味着更多的时间代价和不可控风险，更为可怕的是一旦需要服务器迁移（例如从阿里云迁移到腾讯云），往往需要重新部署和调试，这些琐碎而无趣的“体力活”极大的降低了工作效率。
       而Docker提供了一种更为聪明的方式，通过容器来打包应用，意味着迁移只需要在新的服务器上启动需要的容器就可以了。这无疑将节约大量的宝贵时间，并降低部署过程中出现问题的风险。
    2）Docker在开发和运维中的优势
       对开发和运维人来说，可能最梦寐以求的就是一次性的创建或配置，可以在任意环境，任意时间让应用正常的运行，而Docker恰恰是可以实现这一终极目标的瑞士军刀。
       1）更快速的交付和部署。
          使用Docker，开发人员可以使用镜像来快速的构建一套标准的开发环境：开发完成后，测试和运维人员可以直接使用相同环境来部署代码，Docker可以快速的创建和删除容器，实现快速迭代，大量节约开发，测试，部署时间，并且，各个步骤都有明确的配置和操作，整个过程可见，。
       2）更高效的资源利用
          Docker容器的运行不需要额外的虚拟化管理程序支持，它是内核级的虚拟化，可以实现更高的性能，同时对资源的额外需求很低。
       3）更轻松的迁移和扩展
          Docker容器几乎可以再任意的平台上运行，包括物理机，虚拟机，公有云，私有云，个人电脑，服务器等，这种兼容性让用户可以再不同平台之间轻松的迁移
       5）更简单的更新管理，使用Dockerfile，只需要小小的配置修改 ，就可以替代以往大量的更新工作，并且所有修改都以增量的方式进行分发和更新，从而实现自动化并且高效的容器管理。
</pre>

![](https://i.imgur.com/TN2D6E3.png)

<pre>
Docker与虚拟机比较
   1）Docker容器很快，启动和停止可以在秒级实现，这相比传统的虚拟化方式要快得多。
   2）Docker容器对系统资源需求很少，一台主机上可以同时运行数千个Docker容器
   3）Docker通过类似Git的操作来方便用户获取，分发和更新应用镜像，指令简明，学习成本低
   5）Docker通过Dockerfile配置文件来支持灵活的自动化创建和部署机制，提高工作效率

   传统的虚拟机启动N个不同的应用就启动N个虚拟机，而Docker只需要启动N个隔离的容器，并将应用放到容器中。
   在隔离性方面，传统的虚拟机方式多了一层额外的隔离。但这并不意味着Docker就不安全，Docker利用Linux系统上的多种防护机制实现了严格可靠的隔离。Docker引入了安全选项和镜像机制，极大的提高了使用Docker的安全性。
</pre>

![](https://i.imgur.com/IIY5XZv.png)

<pre>
虚拟化技术
    在计算机技术中，虚拟化是一种资源管理技术，是将计算机的各种实体资源，如服务器，网络，内存，存储等，予以抽象，转换后呈现出来，打破实体结构件的不可切分的障碍，使用可以比原本的组态更好的方式来应用这些资源
    1）完全虚拟化 VMware Workstation 
    2）硬件辅助虚拟化  KVM
    3）部分虚拟化
    5）超虚拟化
    6）操作系统虚拟化   
</pre>

<pre>
Docker镜像
    Docker镜像类似于虚拟机镜像，可以将其理解为一个面向Docker引擎的只读模板，包含了文件系统。
Docker容器
    Docker容器类似于一个轻量级的沙箱，Docker利用容器来运行和隔离应用。
    容器是从镜像创建的应用运行实例，可以将其启动，开始，停止，删除，而这些容器都是相互隔离，可不可见的。
    镜像自身是只读的，容器从镜像启动的时候，Docker会在镜像的最上层创建一个可写层，镜像本身保持不变。
Docker仓库
    Docker仓库类似于代码仓库，是Docker集中存放镜像文件的场所。
    根据是否公开，Docker仓库分为公开仓库和私有仓库。
    当用户创建了自己的镜像之后就可以使用push命令将它上传到指定的公有或者私有仓库，这样用户下次在另外一台机器上使用镜像时时，只需要将其从仓库上pull下来就可以了。
</pre>

<pre>
Docker安装
    Docker支持在主流的操作系平台上使用，包括Ubuntu, CentOS, Windows以及MacOS系统，当然在Linux系列平台上是原生支持，使用体验最好。
</pre>

<pre>
镜像
    镜像时Docker运行容器的前提。
    例如下载一个最新的Ubuntu操作系统
    $ sudo docker pull ubuntu：[tag]  tag为版本号。
    等价于
    $ sudo docker pull registry.hub.docker.com/ubuntu:latest
    下载镜像到本地后，即可随时使用该镜像了，例如利用该镜像创建一个容器，在其中运行bash应用。
    $ sudo docker run -t -i ubuntu bin/bash

    查看镜像信息
    1) 列出本地主机上已有的镜像
    $ sudo docker images

    2）获取镜像的详细信息
    $ sudo docker inspect IMAGE_ID(镜像ID)

    3）搜寻镜像
    $ sudo docker search mysql

    5) 删除镜像 (当一个镜像有多个标签的时候，docker rmi只是删除了该镜像多个标签中的指定标签而已。不影响镜像文件，但当镜像只剩下一个标签的时候就要小心了，此时再使用docker rmi命令会彻底删除该镜像)
    $ sudo docker rmi 
    
    6）查看本机上所有的容器
    $ sudo docker ps -a
</pre>

<pre>
创建镜像
   创建镜像的方法有三种
       1）基于已有镜像的容器创建
          命令  docker commit
          第一步：启动镜像
          $ sudo docker run -ti ubuntu:14.04 /bin/bash
          $ exit

          第二步
          $ sudo docker commit -m 
          commit成功后会返回新创建的镜像的ID

          第三步 查看本地镜像列表，即可看到新创建的镜像
          $ sudo docker images

       2）基于本地模板导入
          也可以直接从一个操作系统模板文件导入一个镜像。
          $ sudo cat | import 
           
       3）基于Dockerfile创建
          
存出和载入镜像
    可以使用docker save 和 docker load命令来存出和载入镜像
    1）如果要存出镜像到本地文件
    $ sudo docker save -o 
   
    2) 载入镜像
    可以使用docker load从存出的本地文件中再导入到本地镜像库
    $ sudo docker load < 
    这将导入镜像以及相关的元数据信息

上传镜像
    可以使用docker push命令上传镜像到仓库，默认上传到DockerHub官方仓库
    $ sudo docker push  
</pre>

<pre>
容器
   容器是镜像的一个运行实例，所不同的是，它带有额外的可写文件层。

   docker create命令创建一个容器
   $ sudo docker create -it 
   $ sudo docker ps -a
   使用docker create创建的容器处于停止状态，可以使用docker start命令来启动它

   新建并启动容器
       启动容器有两种方式
           1）基于镜像新建一个容器并启动
           2）将在终止状态的容器重新启动
       使用的的命令
           docker run 等价于 docker create命令，再执行docker start命令

       当利用docker run来创建并启动容器时，Docker在后台运行的标准操作包括
           1）检查本地是否存在指定的镜像，不存在就从公有仓库下载
           2）利用镜像创建并启动一个容器
           3）分配一个文件系统，并在只读的镜像层外面挂在一层可读写层
           5）从宿主主机配置的网桥接口中桥接一个虚拟接口到容器中去
           6）从地址池配置一个IP地址给容器
           7）执行用户指定的应用程序
           8）执行完毕后容器被终止

       更多的时候需要让Docker容器在后台以守护态形式运行。用户可以通过添加 -d参数来实现。
           $ sudo docker run -d 
           
           终止容器
           使用docker stop来终止一个运行中的容器
           此外当Docker容器中指定的应用终结时，容器也自动终止。
           $ sudo docker stop 

       进入容器
           使用docker attach命令
           docker exec命令
           nsente工具

       删除容器
           docker rm命令删除处于终止状态的容器
           参数 -f 强行终止并删除一个运行中的容器
                -l 删除容器的连接，但保留容器
                -v 删除容器挂载的数据卷

       导出容器
          导出容器是指导出一个已经创建的容器到一个文件，不管此时这个容器是否处于运行状态，可以使用docker export命令
          $ sudo docker export ce5 >test.tar
          可将这些文件传输到其他机器上，在其他机器上通过导入命令实现容器的迁移

       导入容器
          导出的文件又可以使用docker import命令导入，称为镜像。
          $ cat test.tar | sudo docker import 
          实际上，既可以使用docker load命令来导入镜像存储文件到本地的镜像库，又可以使用docker import 命令来导入一个容器快照到本地镜像库。这两者的区别在于容器快照文件将丢弃所有的历史记录和元数据信息，而镜像存储文件将保存完整记录，体积也要大，此外，从容器快照文件导入时可以重新制定标签等元数据信息。 
</pre>

<pre>
仓库
   仓库是集中存放镜像的地方。
   注册服务器（Registry） 
       注册服务器时存放仓库的具体服务器，每个服务器上可以有多个仓库，而每个仓库下面有多个镜像。从这个方面来说，仓库可以被认为是一个具体的项目或目录。
   仓库又分为公共仓库和私有仓库，

Docker Hub
   目前Docker官方维护了一个公共仓库 https://hub.docker.com，其中包括15000多个的镜像。大部分需求都可以通过在Docker Hub中直接下载镜像来实现。

   自动创建功能
       自动创建功能对于需要经常升级镜像内程序来说十分方便，有时候，用户创建了镜像，安装了某个软件，如果软件发布更新则需要手动更新镜像。
       而自动创建功能使得用户通过Docker Hub指定跟踪一个目标网站上的项目，一旦项目发现新的提交，则自动执行创建
</pre>

<pre>
创建和使用私有仓库
    使用registry镜像创建私有仓库
       安装Docker后，可以通过官方提供的registry镜像来简单搭建一套本地私有仓库环境
       $ sudo docker run -d -p 5000：5000 registry
       这将自动下载并启动一个registry容器，创建本地的私有仓库服务
       默认情况下，会将仓库创建在容器的 tmp/registry目录下，可以通过 -v参数来将镜像文件存放在本地的指定路径上。

       此时再本地将启动一个私有仓库服务，监听端口为5000
       使用docker push上传标记的镜像
</pre>

<pre>
数据管理
    用户在使用docker的过程中，往往需要能查看容器内应用产生的数据，或者需要把容器内的数据进行备份，甚至多个容器之间进行数据的共享，这必然涉及容器的数据管理操作。

    数据卷是一个可供容器使用的特殊目录，它绕过文件系统，可以提供很多有用的特性
        1）数据卷可以在容器之间共享和重用
        2）对数据卷的修改会立马生效
        3）对数据卷的更新，不会影响镜像
        5）卷会一直存在，知道没有容器使用
      数据卷的使用，类似于Linux下对目录或文件进行mount操作

      在用docker run命令的时候，使用-v标记可以在容器内创建一个数据卷，多次使用 -v标记可以创建多个数据卷
          1）挂在一个主机目录作为数据卷
          2）挂在一个本地主机文件作为数据卷
    
      数据卷容器
          如果用户需要在容器之间共享一些持续更新的数据，最简单的方式是使用数据卷容器。数据卷容器其实就是一个普通的容器，专门用它来提供数据卷请其他容器挂在使用

      利用数据卷容器迁移数据
          使用如下命令来备份数据
          $ sudo docker run --volumes-from dbdata -v 
          数据恢复
          如果要恢复数据到一个容器，可以按照下面的操作
          $ sudo docker run 
</pre>

<pre>
大量的互联网应用服务包括多个服务组件，这往往需要多个容器之间通过网络通信进行相互配合
    docker目前提供了映射容器端口到宿主主机和容器互联机制来为容器提供网络服务

    从外部访问容器应用
        在启动容器的时候，如果不指定对应参数，在容器外部是无法通过网络来访问容器内的网络应用和服务的。

        当容器中运行一些网络应用，要让外部访问这些应用时，可以通过 -P 或 -p参数来指定端口映射。当使用-P标记时，Docker会随机映射一个 49000 ~ 49900的端口至容器内部开放的网络端口
        $ sudo docker run -d -P
        $ sudo docker ps -l
        此时，可以使用docker ps看到，本地主机的某个端口被映射到了容器的某个端口，访问宿主机的端口即可访问容器内web应用提供的界面
</pre>

<pre>
容器互联实现容器间通信
    容器的连接系统是除了端口映射外另一种可以与容器中应用进行交互的方式，它会在源和接收容器之间创建一个隧道，接收容器可以看到源容器指定的信息

    1）自定义容器命名
       $ sudo docker run -d -P --name
       查看 
       $ sudo docker ps -l

    2）容器互联
       使用 --link参数可以让容器之间安全的进行交互
       第一步 创建一个容器
       $ sudo docker run -d --name db1
       第二步 创建一个容器并与db1互联
       $ sudo docker run -d -P --name web1 --linke db1
       此时 web1与db1建立互联关系
       查看
       $ sudo docker ps
       查看db1容器的names列既有db1,又有web1/db1，表示web1容器连接到db1容器，这允许web1容器访问db1容器的信息

       docker在两个互联的容器之间创建一个安全隧道，而且不用映射他们的端口到宿主机上，在启动db1容器的时候并没有使用 -p和 -P标记，从而避免了暴露数据库端口到外部网络上。

       Docker通过两种方式为容器公开连接信息
           1)环境变量
           2）更新/etc/hosts文件
       使用env命令来查看web容器的环境变量
           $ sudo docker run --rm --name web1 --link db1 .... env
</pre>

<pre>
使用Dockerfile创建镜像
   Dockerfile是一个文本格式的配置文件，用户可以使用Dockerfile快速创建自定义的镜像。

   Dockerfile的基本结构
        Dockerfile由一行命令语句组成，并且支持以#开头的注释行
        一半而言，Dockerfile文件分为四部分
            1）基础镜像信息
            2）维护者信息
            3）镜像操作指令
            5）容器启动时执行指令 

        例如
            
            # 基础镜像
            FROM ubuntu
            # 维护者信息
            MAINTAINER docker_user docker_user@email.com
            # 镜像的操作指令
            RUN echo "" > /etc/apt/sources.list
            RUN apt-get update && apt-get install -y nginx
            RUN echo ""

            # 容器启动时执行指令
            CMD /user/sbin/nginx

创建镜像
    编写完dockerfile之后，可以通过docker build[选项]命令来创建镜像,该命令将读取指定路径下的dockerfile，并将该路径下所有内容发送给Docker服务器，由服务器来创建镜像。
         $ sudo docker build -t mirrorPath dockerfilepath
</pre>

<pre>
Web服务器与应用
    web服务(web service)和web应用(web app)是目前互联网领域的热门技术

    1）创建带Apache服务的Docker镜像
       第一步，创建一个apache-ubuntu工作目录，在其中创建Dockerfile文件，run.sh文件和sample目录
       $ mkdir apache_ubuntu && cd apache_ubuntu
       $ touch Dockerfile run.sh
       $ mkdir sample

       在sample目录下创建index.html文件，内容为
       run.sh脚本内容也很简单,只是启动Apache服务
       #!/bin/bash
       exec apache2 -D FOREGROUND

       创建镜像
           $ sudo docker build -t apache:ubuntu

       在使用Dockerfile创建镜像时，会继承父镜像的开放端口，但却不会集成启动命令。

映射本地目录
    可以通过映射本地目录的方式来指定容器内Apache服务响应的内容

Nginx
    Nginx是一个高性能的Web和反向代理服务器，它具有很多非常优越的特性
    1）作为web服务器，相比apache，Nginx使用更少的资源，支持更多的并发连接，体现更高的的效率，这点使得Nginx尤其受到虚拟主机提供商的欢迎，一个Nginx实例能够轻松支持搞到50000个并发连接数的相应。
    2）作为负载均衡服务器，Nginx既可以在内部直接支持Rails和PHP，也可以支持作为HTTP代理服务器对外进行服务，Nginx用C编写，不论是系统资源开销还是CPU使用效率都比Perbal好得多
    3) 作为邮件代理服务器，Nginx同时也是一个非常优秀的邮件代理服务器，
    5) Nginx安装非常简单，配置文件非常简洁，Bug非常少，Nginx启动特别容器，并且几乎可以做到7 * 24小时不间断运行，还可以在不间断服务的情况下进行软件版本的升级    

使用淘宝的Tengin镜像启动nginx容器    
</pre>

<pre>
构建Docker容器集群
    1）使用自定义网桥连接跨主机容器
       Docker默认的网桥是docker0,它只会在本机连接所有的容器
       在容器中看到的地址一般是像下面这样的地址
</pre>

![](https://i.imgur.com/FoiJ1Ch.png)

![](https://i.imgur.com/xWEWLp4.png)

<pre>
Docker核心技术
   Docker归根到底是一种容器虚拟化技术
   早期版本Docker的底层是基于成熟的Linux Container（LXC）技术实现的，子Docker0.9版本期，Docker除了继续支持LXC格式之外，还开始引入自家的libcontainer，试图打造更通用的底层容器虚拟化库

   从操作系统功能上看，Docker底层依赖的核心技术主要包括Linux操作系统的命名空间（Namespaces）， 控制组(Control Groups), 联合文件系统(Union File Systems)和Linux虚拟网络支持

   基本架构
       Docker采用标准的额C/S架构，包括客户端和服务端两大部分
       客户端和服务端既可以运行在一个机器上，也可以通过socket或者Restful Api来进行通信。

       1）服务端
          Docker Daemon一般在宿主机主机后台运行，作为服务端接收来自客户的请求，并处理这些请求（创建，运行，分发容器），在设计上，Docker daemon是一个非常松耦合的架构，通过专门的Engine模块来分发管理各个来自客户端的任务
       2）客户端
          Docker客户端则为用户提供一系列可执行命令，用户用这些命令实现与Docker Daemon的交互。
          用户使用的Docker可执行命令即为客户端程序，与Docker daemon不同的是 ，客户端发送命令后，等待服务端返回，一旦收到返回后，客户端立刻执行结束并退出。用户执行新的命令，需要再次调用客户端命令。

   命名空间
       命名空间是Linux内核针对实现容器虚拟化而引入的一个强大特性
       每个容器都可以拥有自己单独的命名空间，运行在其中的应用都像是在独立的操作系统中运行一样，命名空间保证了容器之间彼此互不影响。
  
       在操作系统内中，包括内核，文件系统，网络， PID, UID, IPC,内存，硬盘，CPU等资源，所有的资源都是应用进程直接共享的，要想实现虚拟化，除了要实现对内存，CPU,网络IO，硬盘IO，存储空间等的限制外，还要实现文件系统，网络，PID，UID，IPC等等的相互隔离，

       1）进程命名空间
          Linux通过命名空间管理进程号，对于同一个进程，在不同的命名空间中，看到的进程号不相同，每个进程命名空间有一套 自己的进程号管理方法。进程命名空间是一个父子关系的 结构，子空间的进程对于父空间是可见的。新fork出的进程在父命名空年和子命名空间将分别有一个进程号对应。
       2）网络命名空间
          如果有了PID命名空间，那么每个名字空间中的进程就可以相互隔离 ，但是网络端口还是共享本地系统的端口
          通过网络命名空间，可以实现网络隔离，
       3）IPC命名空间
       5）用户命名空间

   控制组
       控制组是Linux内核的一个特性，主要用来对共享资源进行隔离，限制，审计等。只有能控制分配到容器的资源，Docker才能避免多个容器同时运行时的系统资源竞争。

       控制组可以提供对容器的内存，CPU，磁盘I/O 等资源进行限制和计费管理
       控制组的设计目标是为了不同的应用情况提供统一的接口，从控制单一京城到系统级虚拟化
       具体来看，控制组提供如下功能
           1）资源限制
              组可以设置为不超过设定的内存限制，比如：内存子系统可以为进程组设定一个内存使用上限，一旦进程组使用的内存达到限额再申请内存，就会发出Out of Memory告警
           2）优先级
              通过优先级让一些组优先得到更多的CPU等资源
           3）资源审计
              用来统计系统实际上把多少资源用到了适合的目的上，可以使用cpuacct子系统记录某个进程组使用的CPU时间。
           5）隔离
              为组隔离名字空间，这样一个组不会看到另一个组的进程，网络连接和文件系统
           6）控制
              挂起，回复和重启等操作
           sys/fs/cgroup/memory/docker/目录下看到对Docker组应用的各种限制项。

   联合文件系统
      联合文件系统（UnionFs）是一种轻量级的高性能分层文件系统，它支持将文件系统中的修改信息作为一次提交，并层层叠加，同时可以将不同目录挂在到同一个虚拟文件系统系下。

      联合文件系统是实现Docker镜像的技术基础，镜像可以通过分层来进行继承，
          例如。用户基于基础镜像来制作各种不同的应用镜像。这些镜像共享同一个基础镜像层，提高了存储效率。此外，当用户噶比变了一个Docker镜像（比如升级程序到一个新的版本），则一个新的层（layer）会被创建，因此，用户不用替换整个原镜像或者重新建立，只需要添加新层即可。用户分发镜像的时候，也只需要分发被改动的新层内容，这让Docker的镜像管理变得十分轻量级。

          Docker中使用的AUFS(Another  Union File System， 或V2版本往后的 Advanced Multi layer Unification File System)就是一种联合文件系统。AUFS支持为每一个成员目录（类似Git的分支）设定权限。同时AUFS里有一个类似分层的概念，对只读权限的分支可以逻辑上进行增量地修改。
          当Docker利用镜像启动一个容器时，将利用镜像分配文件系统并挂在一个新的可读写的层给容器，容器会在这个文件系统中创建，并且这个可读写的层被添加到镜像中。

   Docker的网络实现
      Docker的网络实现其实就是利用了Linux上的网络命名空间和虚拟网络设备。
      基本原理
          直观上看，要实现网络通信，机器需要至少一个网络接口与外界相通，并可以收发数据包，此外，如果不同子网之间要进行通信，需要额外的路由机制。

          Docker中的网络接口默认都是虚拟的接口，虚拟接口的最大优势就是转发效率高。这是因为Linux通过在内核中进行数据复制来实现虚拟接口之间的数据转发，即发送接口的发送缓存中的数据包被直接复制到接收接口的接收缓存中，而无需通过外部物理设备进行交换，对于本地系统来看，虚拟接口跟一个正常的以太网卡相比并无区别，只是它的速度要快得多。
</pre>

<pre>
Docker安全
    Docker是在Linux操作系统层面上的虚拟化实现，运行在容器内的进程，跟运行在本地系统中的进程，本质上并无区别，不合适的安全策略将可能给本地系统带来风险，因此Docker的安全性在生产环境中十分重要。
    评估Docker的安全性时，主要考虑下面几个方面
        1）Linux内核的命名空间机制提供的容器隔离安全
        2）Linux内核的能力机制所带来的操作权限安全
        3）Linux控制组机制对容器资源的空值能力安全
        5）Docker程序本身的抗攻击性
        6）其他安全增强机制对容器安全性的影响

    1）命名空间隔离的安全
       Docker容器和LXC容器在实现上很相似，所提供的安全特性也基本一致。当用docker run启动一个容器时，Docker将在后台为容器创建一个独立的命名空间。
       
       命名空间提供了最基础也是最直接的隔离，在容器中运行的进程不会被运行在本地主机上的进程和其他容器通过正常渠道发现和影响。

       例如。通过命名空间机制，每个容器都有自己独有的网络栈，以为这它们不能访问其他容器的套接字或接口，当然，容器默认可以与本地主机网络连通，如果主机系统上做了相应的交换设置，容器可以像跟主机交互一项的和其他容器交互。
 
       从网络架构的角度来看，所有的容器实际上是通过本地主机的网桥接口（Docker0）进行通信，就像物理机器通过物理交换机通信一样。

     2）控制组资源控制的安全
       控制组是Linux容器中的另外一个关键组件，它负责实现资源的审计和限制，当用docker run启动一个容器时，Docker在后台为容器创建一个独立的控制组策略组合。
       控制组机制始于2006年，Linux内核从2.6.24版本开始引入 
 
     3）内核能力机制
       能力机制是Linux内核一个强大的特性，可以提供细粒度的权限访问控制。
       Linux内核自2.2版本起支持能力机制，它将权限划分为细粒度的操作能力，既可以作用在进程上，也可以作用在文件上。

     5）Docker服务端的防护
       使用Docker容器的核心是Docker服务端，Docker服务的运行目前还需要root权限的支持，因此服务端安全性十分关键。

       1）必须确保只有可信的用户才能访问Docker服务。
</pre>