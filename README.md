# FuckSogou

#### 这是什么？

- 用途：在Windows系统下，替换并占用搜狗输入法的SogouCloud.exe文件，使其无法弹出广告、且无法被覆盖或删除

- 原理：注册为Windows服务，设置自动启动+失败恢复，可保持程序持续运行，避免被修改

***

#### 如何使用？

1. 确认系统已安装.NET Framework 4.6，到[release](https://github.com/xyh20180101/WlBot/releases)下载所需的文件
2. 找到搜狗输入法安装目录，例如```...\SogouInput\9.5.0.3399```（版本号可能不一样），删掉```SogouCloud.exe```，删不掉的话先结束该进程
3. 把下载的3个文件放到目录下，使用**管理员权限**运行```安装服务.bat```（运行后会产生几个日志文件，可忽略）
4. 打开服务，找到“占用搜狗云文件服务”，右键属性。"常规"：点击启动。"恢复"：把"第一次失败"、"第二次失败"、"后续失败"均设置为"重新启动服务"，以及"在此时间之后重新启动服务"设置为0分钟
5. 服务开始运行，开机自启，进程被结束后会马上重启。如果需要停用，在服务处右键停止或直接卸载服务

***

#### 可能遇到的问题

Q: 运行```安装服务.bat```后，cmd窗口显示```'installutil' 不是内部或外部命令，也不是可运行的程序
或批处理文件。```

A: 尝试找到```C:\Windows\Microsoft.NET\Framework64\v4.0.30319```目录，确认里面有```InstallUtil.exe```这个文件，然后把你自己的目录加到Path环境变量里，或自行修改bat命令