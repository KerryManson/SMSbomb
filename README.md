## 免责声明

本程序仅供娱乐，源码全部开源，**禁止滥用**、**贩卖盈利**、**禁止用于商业用途**。
程序为开源程序，本人不对他人滥用此程序造成的任何结果负任何责任！

## Feature

1. 通过自定义 `api.json` 的方式定义接口.  
2. 支持关键字替换. **时间戳** `[timestamp]` **手机号** `[phone]`  
3. 多线程/异步 请求.  
4. 通过 Flask 提供网页测试/添加接口.  
5. 友好的命令行参数支持.  
6. 采用方便的 pipenv 包管理.  

## Quick Start

### windows教程

1. 进入[release](https://github.com/52marvelous/SMSbomb/releases)，下载最新的发行版！
2. 把可执行文件放在任意目录
   ![](C:/Users/zlp/Desktop/%E6%96%B0%E5%BB%BA%E6%96%87%E4%BB%B6%E5%A4%B9/SMSBoom/rawI5xCA3RGmMiy-165456257554210.png)
3. 进入CMD命令行
   ![](C:/Users/zlp/Desktop/%E6%96%B0%E5%BB%BA%E6%96%87%E4%BB%B6%E5%A4%B9/SMSBoom/JZTm1ekX8n3wzqA-165456257554212.png)
   ![](C:/Users/zlp/Desktop/%E6%96%B0%E5%BB%BA%E6%96%87%E4%BB%B6%E5%A4%B9/SMSBoom/UL1OQuVl8S2tF6e.png)
4. 输入命令开始玩耍即可！

#### 命令示例

更新接口

```powershell
smsboom_pyinstall.exe update
```

启动64个线程,轰//炸一个人的手机号(198xxxxxxxx),只轰//炸一波。

```powershell
smsboom_pyinstall.exe run -t 64 -p 198xxxxxxxxx
```

启动64个线程,轰//炸多个人的手机号(19xxxxxxx),启动循环轰//炸，每个循环间隔60秒

```powershell
smsboom_pyinstall.exe run -t 64 -p 198xxxxxxxxx -s -i 60
```

启动64个线程,轰//炸多个人的手机号(138xxx,139xxxx),启动循环轰//炸,每个循环间隔60秒。

```powershell
smsboom_pyinstall.exe run -t 64 -p 138xxxxxxxx -p 139xxxxxxxx -s -i 60
```

### 命令行 / Linux部署教程

为了安全起见，建议选用国外云服务器进行测试和玩耍！
我使用的是centos系统！

#### 安装python3

centos默认安装的python2，我们需要安装python3.x才能正常使用项目！

1. 安装依赖包

```shell
yum install zlib-devel bzip2-devel openssl-devel ncurses-devel sqlite-devel readline-devel tk-devel gcc make libffi-devel
```

2. 安装wget

```shell
yum install wget
```

3. 下载python3.x源码

```shell
wget https://www.python.org/ftp/python/3.8.1/Python-3.8.1.tgz
```

4. 解压并安装

```shell
# 解压压缩包
tar -zxvf Python-3.8.1.tgz  
# 进入文件夹
cd Python-3.8.1
# 配置安装位置
./configure prefix=/usr/local/python3
# 安装
make && make install
```

5. 添加软连接

```shell
#添加python3的软链接 
ln -s /usr/local/python3/bin/python3.8 /usr/bin/python3 
#添加 pip3 的软链接 
ln -s /usr/local/python3/bin/pip3.8 /usr/bin/pip3
```

6. 安装pipenv

```shell
pip3 install pipenv
```

7. 添加环境变量

```shell
vim /etc/profile
#在文件中添加如下一行
export PATH=$PATH:/usr/local/python3/bin
#保存并退出后之刷新
source /etc/profile
```

#### 部署工具

1. 克隆项目

   ```shell
   git clone https://github.com/AdminWhaleFall/SMSBoom.git
   ```

2. 为项目构建环境并激活环境

   ```shell
   pipenv install  # 仅使用轰//炸功能
   pipenv install --dev # 使用 webui 调试接口功能.
   pipenv shell # 激活虚拟环境
   ```

3. 激活虚拟环境后就可以玩耍了！

#### 命令示例

更新接口

```shell
python smsboom.py update
```

启动64个线程,轰//炸一个人的手机号(198xxxxxxxx),只轰//炸一波。

```shell
python smsboom.py run -t 64 -p 198xxxxxxxxx
```

启动64个线程,轰//炸多个人的手机号(19xxxxxxx),启动循环轰//炸，每个循环间隔60秒

```shell
python smsboom.py run -t 64 -p 198xxxxxxxxx -s -i 60
```

启动64个线程,轰//炸多个人的手机号(138xxx,139xxxx),启动循环轰//炸,每个循环间隔60秒。

```shell
python smsboom.py run -t 64 -p 138xxxxxxxx -p 139xxxxxxxx -s -i 60
```

### Flask 前端调试

> **前提是已经根据前文 Quick Start 的方式安装好 pipenv 环境**

```shell
pipenv shell # 激活虚拟环境
python run_flask_app.py start -p 9090 # 监听9090端口
```

**运行帮助:**

```shell
Usage: run_flask_app.py [OPTIONS] COMMAND [ARGS]...

Options:
  --help  Show this message and exit.

Commands:
  init         初始化数据库
  json2sqlite  将json数据转为sqlite数据库
  sqlite2json  将sqlite数据转为json
  start        启动 flask app
Usage: run_flask_app.py start [OPTIONS]

  启动 flask app

Options:
  -h, --host TEXT     监听地址
  -p, --port INTEGER  监听端口
  --help              Show this message and exit.
```

默认监听 *0.0.0.0:9090* 地址,浏览器访问http://127.0.0.1:9090/admin 若无意外,就可以出现前端调试界面。

## 讨论

TG群：https://t.me/+QVyYZYL0hVhhOTI9

QQ群：765307424

可以在QQ群或者TG讨论或者获得帮助！

更多资源和教程可以关注：[天宇博客](https://www.tingfengge.online/)

我们的收费QQ群：810074782

收费10元，群内更新各种软件和教程！本收费群与本项目无关！
