## spark安装

### 在本地机器上部署docker

安装docker，macOS支持用Homebrew来安装docker方式安装 [macOs上安装docker](https://www.runoob.com/docker/macos-docker-install.html) 安装过程可以参考上述博客;

### git项目文件到本地机器
git文件到本地，我们使用欧洲大数据平台的资源[https://github.com/big-data-europe/docker-hadoop-spark-workbench](https://github.com/big-data-europe/docker-hadoop-spark-workbench)。

```markdown
- 打开终端，利用git命令下载文件到本机
git clone https://github.com/big-data-europe/docker-hadoop-spark-workbench.git

- 报错如下
Cloning into 'docker-spark'...
remote: Enumerating objects: 39, done.
remote: Counting objects: 100% (39/39), done.
remote: Compressing objects: 100% (31/31), done.
error: RPC failed; curl 56 LibreSSL SSL_read: SSL_ERROR_SYSCALL, errno 54
fatal: the remote end hung up unexpectedly
fatal: early EOF
fatal: index-pack failed

- 修改大小限制
git init
git config http.postBuffer 524288000
git clone https://github.com/big-data-europe/docker-hadoop-spark-workbench.git
```

### 运行Docker-compose文件

git下来之后将会放入本地目录之中，我的目录文件为/Users/danieltse/代码/hive/docker-hadoop-spark-workbench，进入后开始一个新的HDFS/Spark Workbench
```markdown
docker-compose up -d
```
会显示 Create network "docker-hadoop-spark-workbench_default" with default driver 
成功~

开始Hive工作台支持，检查已有服务已经运行完毕
```markdown
docker-compose -f docker-compose-hive.yml up -d namenode hive-metastore-postgresql
docker-compose -f docker-compose-hive.yml up -d datanode hive-metastore
docker-compose -f docker-compose-hive.yml up -d hive-server
docker-compose -f docker-compose-hive.yml up -d spark-master spark-worker spark-notebook hue
```




