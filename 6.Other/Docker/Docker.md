[toc]

### 环境

![20201227153010](http://pic.sigalx.com/pic/20201227153010.png)

![20201227153030](http://pic.sigalx.com/pic/20201227153030.png)

### 安装 Docker

```shell
# 1. 删除旧的docker
yum remove docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-engine

# 2. 安装基本环境
yum install -y yum-utils

# 3. 配置仓库,官方仓库很慢,可以使用阿里仓库
yum-config-manager \
    --add-repo \
    https://download.docker.com/linux/centos/docker-ce.repo      # (官方仓库)

    or

    http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo # (阿里云仓库)

# 4. 安装docker engine
yum install docker-ce docker-ce-cli containerd.io

# 5. 启动docker
systemctl start docker

# 6. 查看版本 -- 安装成功
docker version

# 7. 测试
docker run hello-world
```

![20201228152536](http://pic.sigalx.com/pic/20201228152536.png)

### 卸载 Docker

```shell
# 1. 卸载依赖
yum remove docker-ce docker-ce-cli containerd.io

# 2. 删除文件
rm -rf /var/lib/docker
```

### Docker 常用命令

###### **docker version**

查看版本信息

```shell
 Version:           20.10.1
 API version:       1.41
 Go version:        go1.13.15
 Git commit:        831ebea
 Built:             Tue Dec 15 04:34:30 2020
 OS/Arch:           linux/amd64
 Context:           default
 Experimental:      true

Server: Docker Engine - Community
 Engine:
  Version:          20.10.1
  API version:      1.41 (minimum version 1.12)
  Go version:       go1.13.15
  Git commit:       f001486
  Built:            Tue Dec 15 04:32:21 2020
  OS/Arch:          linux/amd64
  Experimental:     false
 containerd:
  Version:          1.4.3
  GitCommit:        269548fa27e0089a8b8278fc4fc781d7f65a939b
 runc:
  Version:          1.0.0-rc92
  GitCommit:        ff819c7e9184c13b7c2607fe6c30ae19403a7aff
 docker-init:
  Version:          0.19.0
  GitCommit:        de40ad0
```

###### docker info

查看 docker 信息

```shell
Client:
 Context:    default
 Debug Mode: false
 Plugins:
  app: Docker App (Docker Inc., v0.9.1-beta3)
  buildx: Build with BuildKit (Docker Inc., v0.5.0-docker)

Server:
 Containers: 4
  Running: 0
  Paused: 0
  Stopped: 4
 Images: 1
 Server Version: 20.10.1
 Storage Driver: overlay2
  Backing Filesystem: extfs
  Supports d_type: true
  Native Overlay Diff: true
 Logging Driver: json-file
 Cgroup Driver: cgroupfs
 Cgroup Version: 1
 Plugins:
  Volume: local
  Network: bridge host ipvlan macvlan null overlay
  Log: awslogs fluentd gcplogs gelf journald json-file local logentries splunk syslog
 Swarm: inactive
 Runtimes: io.containerd.runc.v2 io.containerd.runtime.v1.linux runc
 Default Runtime: runc
 Init Binary: docker-init
 containerd version: 269548fa27e0089a8b8278fc4fc781d7f65a939b
 runc version: ff819c7e9184c13b7c2607fe6c30ae19403a7aff
 init version: de40ad0
 Security Options:
  seccomp
   Profile: default
 Kernel Version: 4.18.0-80.el8.x86_64
 Operating System: CentOS Linux 8 (Core)
 OSType: linux
 Architecture: x86_64
 CPUs: 1
 Total Memory: 1.787GiB
 Name: VM-0-4-centos
 ID: 4PUL:G53N:OIMO:F5AH:N6JZ:HWDT:VVHW:RGKG:I3RY:5YW4:E2GM:IHC5
 Docker Root Dir: /var/lib/docker
 Debug Mode: false
 Registry: https://index.docker.io/v1/
 Labels:
 Experimental: false
 Insecure Registries:
  127.0.0.0/8
 Live Restore Enabled: false
```
###### docker stats

查看状态

###### **docker images --help**

获取命令的帮助

```shell
Usage:  docker images [OPTIONS] [REPOSITORY[:TAG]]

List images

Options:
  -a, --all             Show all images (default hides intermediate images)
      --digests         Show digests
  -f, --filter filter   Filter output based on conditions provided
      --format string   Pretty-print images using a Go template
      --no-trunc        Don't truncate output
  -q, --quiet           Only show image IDs
```

##### 镜像命令

###### **docker images**

查看已下载镜像,经常用的市 -aq

```shell
REPOSITORY    TAG       IMAGE ID       CREATED         SIZE
hello-world   latest    bf756fb1ae65   11 months ago   13.3kB
```

REPOSITORY: 镜像仓库源

TAG: 镜像的标签

IMAGE ID: 镜像 ID

CREATED: 镜像创建时间

SIZE: 镜像大小

###### **docker search**

搜索镜像

`docker search nginx --filter stars=9000`,搜索 start 大于或等于 9000 start 的镜像

###### **docker pull**

下载镜像

`docker pull nginx or docker pull nginx:1.1`

```shell
Using default tag: latest                          # 如果不写 tag 默认就是最新的版本
latest: Pulling from library/nginx
6ec7b7d162b2: Pull complete                        # 分层下载, 联合文件系统
cb420a90068e: Pull complete
2766c0bf2b07: Pull complete
e05167b6a99d: Pull complete
70ac9d795e79: Pull complete
Digest: sha256:4cf620a5c81390ee209398ecc18e5fb9dd0f5155cd82adcbae532fec94006fb9
                                                   # 签名和防伪标志
Status: Downloaded newer image for nginx:latest
docker.io/library/nginx:latest                     # 真实地址
```

###### docker rmi

删除镜像

`docker rmi 镜像id或名称 镜像id或名称 镜像id或名称`: 删除一个或多个镜像,空格隔开

`docker rmi -f $(docker images -aq)`: 删除全部镜像

##### 容器命令

有了镜像才能创建容器

###### docker run

启动镜像新建容器

`docker run -it nginx`: -it 使用交互方式运行,直接进入容器

`docker run -d nginx`: -d 以后台方式运行

`docker run -p 3305:3306 nginx`: -p 挂在端口 -P随机挂载端口
dd

ps:

使用`docker run -it --rm nginx:版本` 要是没这个镜像的话,会自动下载并启动 

-rm:用完即删除,一般测试用

###### docker ps

`docker ps`: 显示正在运行的容器

`docker ps -a`: 显示全部运行的容器,也会显示曾经运行过的容器

`docker ps -a -n=1`: 显示最近的 一个 创建的容器

`docker ps -aq`: 和镜像一样可以 aq 用

###### 退出容器

`exit` 退出并停止容器

`Ctrl + p + q` 退出不停止容器

###### docker rm

删除容器

`docker rm`: 删除容器,不能删除正在运行的容器

`docker rm -f`: 可以删除正在运行的容器

`docker rm -f $(docker ps -aq)`: 和镜像一样,删除全部容器

###### 容器启动停止等操作

```shell
docker start 容器id            # 启动容器
docker stop 容器id             # 停止容器
docker restart 容器id          # 重启容器
docker kill 容器id             # 强制停止容器
```

###### docker logs

查看容器日志

`docker logs -tf -tail 10 容器id`

-t: 带上时间戳

-f: 跟踪显示, 如果有往日志写东西, 实时的显示出来

--tail number: 显示几行

###### docker top

查看容器中进程信息

`docker top 容器id`

```shell
UID                 PID                 PPID                C                   STIME               TTY                 TIME                CMD
root                105789              105769              0                   01:55               pts/0               00:00:00            /bin/bash
```
###### docker inspect

查看容器的元数据

`docker inspect 容器id`

```shell
[
    {
        "Id": "a088ec7c82eb29e3e8051a6c4d9c73eedae13694ac38fcc13f9e0f00512f591d",
        "Created": "2020-12-27T17:55:15.749117088Z",
        "Path": "/bin/bash",
        "Args": [],
        "State": {
            "Status": "running",
            "Running": true,
            "Paused": false,
            "Restarting": false,
            "OOMKilled": false,
            "Dead": false,
            "Pid": 105789,
            "ExitCode": 0,
            "Error": "",
            "StartedAt": "2020-12-27T17:55:16.122011097Z",
            "FinishedAt": "0001-01-01T00:00:00Z"
        },
        "Image": "sha256:300e315adb2f96afe5f0b2780b87f28ae95231fe3bdd1e16b9ba606307728f55",
        "ResolvConfPath": "/var/lib/docker/containers/a088ec7c82eb29e3e8051a6c4d9c73eedae13694ac38fcc13f9e0f00512f591d/resolv.conf",
        "HostnamePath": "/var/lib/docker/containers/a088ec7c82eb29e3e8051a6c4d9c73eedae13694ac38fcc13f9e0f00512f591d/hostname",
        "HostsPath": "/var/lib/docker/containers/a088ec7c82eb29e3e8051a6c4d9c73eedae13694ac38fcc13f9e0f00512f591d/hosts",
        "LogPath": "/var/lib/docker/containers/a088ec7c82eb29e3e8051a6c4d9c73eedae13694ac38fcc13f9e0f00512f591d/a088ec7c82eb29e3e8051a6c4d9c73eedae13694ac38fcc13f9e0f00512f591d-json.log",
        "Name": "/determined_easley",
        "RestartCount": 0,
        "Driver": "overlay2",
        "Platform": "linux",
        "MountLabel": "",
        "ProcessLabel": "",
        "AppArmorProfile": "",
        "ExecIDs": null,
        "HostConfig": {
            "Binds": null,
            "ContainerIDFile": "",
            "LogConfig": {
                "Type": "json-file",
                "Config": {}
            },
            "NetworkMode": "default",
            "PortBindings": {},
            "RestartPolicy": {
                "Name": "no",
                "MaximumRetryCount": 0
            },
            "AutoRemove": false,
            "VolumeDriver": "",
            "VolumesFrom": null,
            "CapAdd": null,
            "CapDrop": null,
            "CgroupnsMode": "host",
            "Dns": [],
            "DnsOptions": [],
            "DnsSearch": [],
            "ExtraHosts": null,
            "GroupAdd": null,
            "IpcMode": "private",
            "Cgroup": "",
            "Links": null,
            "OomScoreAdj": 0,
            "PidMode": "",
            "Privileged": false,
            "PublishAllPorts": false,
            "ReadonlyRootfs": false,
            "SecurityOpt": null,
            "UTSMode": "",
            "UsernsMode": "",
            "ShmSize": 67108864,
            "Runtime": "runc",
            "ConsoleSize": [
                0,
                0
            ],
            "Isolation": "",
            "CpuShares": 0,
            "Memory": 0,
            "NanoCpus": 0,
            "CgroupParent": "",
            "BlkioWeight": 0,
            "BlkioWeightDevice": [],
            "BlkioDeviceReadBps": null,
            "BlkioDeviceWriteBps": null,
            "BlkioDeviceReadIOps": null,
            "BlkioDeviceWriteIOps": null,
            "CpuPeriod": 0,
            "CpuQuota": 0,
            "CpuRealtimePeriod": 0,
            "CpuRealtimeRuntime": 0,
            "CpusetCpus": "",
            "CpusetMems": "",
            "Devices": [],
            "DeviceCgroupRules": null,
            "DeviceRequests": null,
            "KernelMemory": 0,
            "KernelMemoryTCP": 0,
            "MemoryReservation": 0,
            "MemorySwap": 0,
            "MemorySwappiness": null,
            "OomKillDisable": false,
            "PidsLimit": null,
            "Ulimits": null,
            "CpuCount": 0,
            "CpuPercent": 0,
            "IOMaximumIOps": 0,
            "IOMaximumBandwidth": 0,
            "MaskedPaths": [
                "/proc/asound",
                "/proc/acpi",
                "/proc/kcore",
                "/proc/keys",
                "/proc/latency_stats",
                "/proc/timer_list",
                "/proc/timer_stats",
                "/proc/sched_debug",
                "/proc/scsi",
                "/sys/firmware"
            ],
            "ReadonlyPaths": [
                "/proc/bus",
                "/proc/fs",
                "/proc/irq",
                "/proc/sys",
                "/proc/sysrq-trigger"
            ]
        },
        "GraphDriver": {
            "Data": {
                "LowerDir": "/var/lib/docker/overlay2/56b5659784b00bace7b85263952272eb834f1e63dc831fb908c841ad8502ed98-init/diff:/var/lib/docker/overlay2/354b7b59fb731e9c1ebda558bf4bd739e82982c2fc11aac4ee64b2a1a3261bf7/diff",
                "MergedDir": "/var/lib/docker/overlay2/56b5659784b00bace7b85263952272eb834f1e63dc831fb908c841ad8502ed98/merged",
                "UpperDir": "/var/lib/docker/overlay2/56b5659784b00bace7b85263952272eb834f1e63dc831fb908c841ad8502ed98/diff",
                "WorkDir": "/var/lib/docker/overlay2/56b5659784b00bace7b85263952272eb834f1e63dc831fb908c841ad8502ed98/work"
            },
            "Name": "overlay2"
        },
        "Mounts": [],
        "Config": {
            "Hostname": "a088ec7c82eb",
            "Domainname": "",
            "User": "",
            "AttachStdin": true,
            "AttachStdout": true,
            "AttachStderr": true,
            "Tty": true,
            "OpenStdin": true,
            "StdinOnce": true,
            "Env": [
                "PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"
            ],
            "Cmd": [
                "/bin/bash"
            ],
            "Image": "centos",
            "Volumes": null,
            "WorkingDir": "",
            "Entrypoint": null,
            "OnBuild": null,
            "Labels": {
                "org.label-schema.build-date": "20201204",
                "org.label-schema.license": "GPLv2",
                "org.label-schema.name": "CentOS Base Image",
                "org.label-schema.schema-version": "1.0",
                "org.label-schema.vendor": "CentOS"
            }
        },
        "NetworkSettings": {
            "Bridge": "",
            "SandboxID": "fed5fc08ee67e6247949ca9dd3ad9f7a077fd79750f39dd9af898a3419e39c54",
            "HairpinMode": false,
            "LinkLocalIPv6Address": "",
            "LinkLocalIPv6PrefixLen": 0,
            "Ports": {},
            "SandboxKey": "/var/run/docker/netns/fed5fc08ee67",
            "SecondaryIPAddresses": null,
            "SecondaryIPv6Addresses": null,
            "EndpointID": "d4792bffcb39235c1474043de89d5db829d6e8127fd2835ca06cedfefa5e0a0c",
            "Gateway": "172.17.0.1",
            "GlobalIPv6Address": "",
            "GlobalIPv6PrefixLen": 0,
            "IPAddress": "172.17.0.2",
            "IPPrefixLen": 16,
            "IPv6Gateway": "",
            "MacAddress": "02:42:ac:11:00:02",
            "Networks": {
                "bridge": {
                    "IPAMConfig": null,
                    "Links": null,
                    "Aliases": null,
                    "NetworkID": "c9eb27dd8d7bc3e4275a2bec7121956d04e7434c6dc7e71ec0c063bc1e5ac07c",
                    "EndpointID": "d4792bffcb39235c1474043de89d5db829d6e8127fd2835ca06cedfefa5e0a0c",
                    "Gateway": "172.17.0.1",
                    "IPAddress": "172.17.0.2",
                    "IPPrefixLen": 16,
                    "IPv6Gateway": "",
                    "GlobalIPv6Address": "",
                    "GlobalIPv6PrefixLen": 0,
                    "MacAddress": "02:42:ac:11:00:02",
                    "DriverOpts": null
                }
            }
        }
    }
]
```

###### docker exec or docker attach

进入正在运行的容器

`docker exec -it 容器id /bin/bash` or `docker attach 容器id`

区别:

docker exec 进入容器后开启一个新的终端或进程,可以在里面操作

docker attach 进入容器后直接在正在执行的终端,不会启动新的进程

###### 从容器内拷贝文件到主机上

`docker cp 容器id:容器文件地址 目的地址`

`docker cp 容器id:/home/sigal.php /home`: 将容器内/home/sigal.php文件拷贝到主机/home中

ps:

容器启动不启动没关系,只要容器在,数据就在


docker run -d --name nginxtest -p 8080:80 nginx : 启动 nginx


### 打包自己的镜像

docker commit -m="提交描述信息" -a="作者" 容器id 目标镜像名:[tag]

1. 启动一个容器

2. 操作容器

3. 将操作过的容器通过 commit 提交到为一个新的镜像


### 使用容器卷

docker run -it -v 主机目录:容器内目录

![20201228133319](http://pic.sigalx.com/pic/20201228133319.png)

匿名挂载和具名挂载

### dockerfile

![20201228143911](http://pic.sigalx.com/pic/20201228143911.png)

![20201228144105](http://pic.sigalx.com/pic/20201228144105.png)

![20201228144228](http://pic.sigalx.com/pic/20201228144228.png)

![20201228144902](http://pic.sigalx.com/pic/20201228144902.png)