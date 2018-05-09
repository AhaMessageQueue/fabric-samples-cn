# e2e_cli

> 💡 确保你已经读完了[README.md](https://github.com/fnpac/fabric-samples-cn/blob/master/README.md)

## 特性

* 该脚本基于docker-compose在**一台机器**上创建fabric网络；
* fabric网络结构包括：2个Org（分别有2个Peer）、1个Cli、1个Orderer（3个Zookeeper以及4个Kafka）；
* 适合快速构建并测试fabric区块链网络；

> 💡 该脚本构建fabric区块链网络所使用的二进制文件，是基于`fabric`源码构建的，所以务必确保`fabric-samples-cn`文件夹与`fabric`源码文件夹处于同一目录下。

## 操作fabric

直接运行该脚本即可创建fabric网络。

```text
./network_setup.sh up
```

### 关闭网络

主要执行如下内容：

* 删除Compose文件中定义的容器
* 删除Compose文件中`networks`部分定义的网络
* 删除docker中的所有容器
* 删除链码镜像
* 删除通过`cryptogen`生成的MSP身份证书
* 删除通过`configtxgen`工具生成的创世区块、应用通道配置交易文件、锚节点配置更新文件
* 删除fabric的整个区块链账本数据

```bash
./network_setup.sh down
```

### 重启网络

```bash
./network_setup.sh restart
```

> 💡 重启操作实际是先后执行了`./network_setup.sh down`与`./network_setup.sh up`两个操作。