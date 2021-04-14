安装BOT
申请API_ID及API_HASH
打开 my.telegram.org
登录
创建API
![image](https://user-images.githubusercontent.com/44235578/114650410-c847fd80-9d14-11eb-8539-53420e97f132.png)

API名称
![image](https://user-images.githubusercontent.com/44235578/114650379-bebe9580-9d14-11eb-9312-4f23a9962335.png)

创建好的API如下
![image](https://user-images.githubusercontent.com/44235578/114650433-d138cf00-9d14-11eb-9310-85b3cc2e6bb1.png)

下载文件
必要文件：

 - bot.json       //【必须】配置文件
 - bot.py         //【必须】v4版docker，用botV4.py
 - rebot.sh       //【必须】v4版docker，用rebotV4.sh
 - shortcut.list  //【可选】自定义按钮
文件下载：下载地址

修改bot.json文件
将bot.json文件修改为如下格式，注意红框部分无引号项。
![image](https://user-images.githubusercontent.com/44235578/114650448-d72eb000-9d14-11eb-998c-ff2d8ef0bbee.png)

上传修改文件
V3上传修改后的bot.json、bot.py和rebot.sh文件上传至容器内的/jd/config文件夹。
V4上传修改后的bot.json、botV4.py和rebotV4.sh文件上传至容器内的/jd/config文件夹。
进入容器
docker exec -it 容器名 bash
安装python环境
安装python3及pip
apk update
apk add python3
apk add py2-pip
注意：【可选操作】网络较差时，可以尝试切换至清华源安装依赖，命令如下：

pip3 config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple
或
pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple
安装依赖及模块
方法一：适合懒人
下载requirements.txt文件
wget https://raw.githubusercontent.com/SuMaiKaDe/jddockerbot/master/requirements.txt
安装依赖及模块
pip3 install -r requirements.txt
或
pip install -r requirements.txt
注意：当遇到缺模块或模块版本不匹配问题，使用方法二手动补充所缺模块

方法二：适合勤快人
安装依赖
apk add zlib-dev gcc jpeg-dev python3-dev musl-dev
安装模块
pip install --upgrade pip
pip install requests telethon python-socks[asyncio] pillow qrcode
注意：命令行中黄色字为警告，红色字表示报错。如果pip install，遇到报错【红色字】，可以尝试如下命令：

pip3 install requests telethon python-socks[asyncio] pillow qrcode
运行BOT机器人
V4版本

python3 botV4.py
V3版本

python3 bot.py
docker后台运行机器人
V4版本
bash rebotV4.sh
V3版本
bash rebot.sh
设置容器启动自动运行BOT
将命令添加到diy.sh

V4版本
bash /jd/config/rebotV4.sh
V3版本
bash /jd/config/rebot.sh
进阶教程
使用自定义按钮
在/jd/config文件夹，创建 shortcut.list 文件
修改 shortcut.list，添加自定义按钮，格式如下：
更新脚本-->jup
京豆通知-->jtask jd_bean_change
解析：

中文为 按钮名称
-->后 红字为 按钮命令
