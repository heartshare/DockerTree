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
           1）检查本地是否存在指定的镜像。
</pre>