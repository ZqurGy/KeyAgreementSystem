# 项目部署

## 服务端部署

### 1、 配置环境

1. openssl安装

   ```shell
   # 克隆openssl
   git clone git://git.openssl.org/openssl.git
   
   # 解压文件
   .tar.gz格式:tar -zxvf openssl.tar.gz
   .zip格式:unzip openssl.zip
   
   # 编译安装
   ./config
   make
   make test       （可选）
   make install     (使用管理员权限执行该命令)
   
   # 验证是否安装成功
   openssl version -a
   
   # 如果没有安装成功,一般都是动态库找不到
   vim /etc/ld.so.conf --> 添加一下动态库路径
   sudo ldconfig --> 路径生效
   ```

2. Oracle安装

   >  参考文章：https://juejin.cn/post/7220775341604847674

3. 配置OCCI库

   ```shell
   ## 请把已经环境变量设置到对应的文件中
   vim Hi-看我,看我.sh
   
   ## 导入环境变量
   # 可以是当前用户的 ~/.bashrc文件, 也可以是系统的 /etc/profile文件
   # OCCI_HOME 该环境变量的路径需要做对应修改
   export OCCI_HOME=/opt/instantclient_11_2 # 解压位置
   export OCCI_INCLUDE_DIR=$OCCI_HOME/sdk/include
   export OCCI_LIBRARY_PATH=$OCCI_HOME 
   export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$OCCI_LIBRARY_PATH
   # 程序编译是搜索的库目录
   export LIBRARY_PATH=$LIBRARY_PATH:$OCCI_LIBRARY_PATH
   # 程序编译时搜索的头文件目录
   export CPLUS_INCLUDE_PATH=$CPLUS_INCLUDE_PATH:$OCCI_INCLUDE_DIR
   
   ## 生效
   source ./.bashrc 或者 source /etc/profile
   ```

### 2、 编译程序

```shell
make
```

### 3、 执行程序

需要先对数据库导入表和网点数据

## 客户端部署

### 1、 配置环境

1. openssl安装

   ```shell
   # 克隆openssl
   git clone git://git.openssl.org/openssl.git
   
   # 解压文件
   .tar.gz格式:tar -zxvf openssl.tar.gz
   .zip格式:unzip openssl.zip
   
   # 编译安装
   ./config
   make
   make test       （可选）
   make install     (使用管理员权限执行该命令)
   
   # 验证是否安装成功
   openssl version -a
   
   # 如果没有安装成功,一般都是动态库找不到
   vim /etc/ld.so.conf --> 添加一下动态库路径
   sudo ldconfig --> 路径生效
   ```

### 2、 编译程序

```shell
make
```

