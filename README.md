## 自用的一个docker上的shadowsocks脚本（v0.1测试版）
> docker image链接：https://hub.docker.com/r/teddysun/shadowsocks-libev

本脚本是在这个image的基础上编写，为了便利使用，细节未优化，仅供自用。


本脚本使用方法：
```
wget https://raw.githubusercontent.com/magic233/shadowsocks_docker/master/shadowsocks_docker
chmod +x shadowsocks_docker.sh
./shadowsocks_docker.sh
```

1. Install shadowsocks
2. Start shadowsocks
3. Stop shadowsocks
4. View port&password
5. Stop&Remove shadowsocks images

Install shadowsocks：必须在邮docker环境的基础下才可以安装

Start shadowsocks: 必须用本脚本安装过shadowsocks的情况下关闭（容器未删除）才可用次选项启动

Stop shadowsocks：停止shadowsocks

View port&password：用脚本安装完成后会自动创建缓存文件，用此选项可读取配置信息

Stop&Remove shadowsocks images：停止并删除容器以及镜像


```
./shadowsocks.sh   //可再次启用脚本
```

