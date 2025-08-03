# 懒猫微服备份比亚迪行车记录仪

[TOC]

![image-20250605025813563](https://lzc-playground-1301583638.cos.ap-chengdu.myqcloud.com/guidelines/395/20250605030007806.png?imageSlim)

## 1、准备工作

### 1、参考这篇文章配置

把微服的webdav转发到公网进行访问

1. https://github.com/wlabby-1/cloudflared-helper（猫猫不要开科学上网，跟cf会有冲突）
2. 具体详细配置请参考截图

![image-20250605013115802](https://lzc-playground-1301583638.cos.ap-chengdu.myqcloud.com/guidelines/395/20250605030007622.png?imageSlim)

![image-20250605013221340](https://lzc-playground-1301583638.cos.ap-chengdu.myqcloud.com/guidelines/395/20250605030007662.png?imageSlim)

### 2、安装备份软件

使用U盘把[foldersync.apk](https://github.com/wlabby-1/bydcartravelerrecordbackup/blob/main/foldersync.apk)这个安装包安装到比亚迪车机系统里，并在设置里授权

<img src="https://lzc-playground-1301583638.cos.ap-chengdu.myqcloud.com/guidelines/395/20250605030007705.png?imageSlim" alt="image-20250605012435084" style="zoom: 67%;" /> 

<img src="https://lzc-playground-1301583638.cos.ap-chengdu.myqcloud.com/guidelines/395/20250605030007867.png?imageSlim" alt="image-20250605013258739" style="zoom: 50%;" /> 

## 2、进行配置

### 1、添加账户设置

打开foldersync之后，点击中间用户——>添加用户——>选择webdav

![image-20250605021733608](https://lzc-playground-1301583638.cos.ap-chengdu.myqcloud.com/guidelines/395/20250605030007689.png?imageSlim)   

#### 1、配置填写

```bash
在用户名和密码处填写：懒猫网盘——>点击右上角头像处——>点击设置——>网络服务——>WebDAV的用户名和密码
服务器地址：填写上一步用cf转出来的公网地址（不需要http&https）
端口：443
路径：/dav
高级：全部勾选
身份验证：Basic
```

![image-20250605022407067](https://lzc-playground-1301583638.cos.ap-chengdu.myqcloud.com/guidelines/395/20250605030008721.png?imageSlim))

填写完成之后点击测试

![image-20250605022443321](https://lzc-playground-1301583638.cos.ap-chengdu.myqcloud.com/guidelines/395/20250605030008680.png?imageSlim)   

### 2、添加配置同步

配置测试通过之后，点击添加文件夹对

![image-20250605022503946](https://lzc-playground-1301583638.cos.ap-chengdu.myqcloud.com/guidelines/395/20250605030008700.png?imageSlim)   

添加完成之后给您的文件夹对取个名字

![image-20250605022532948](https://lzc-playground-1301583638.cos.ap-chengdu.myqcloud.com/guidelines/395/20250605030008696.png?imageSlim) 

根据实际需求选择一个同步引擎（建议V2）

![image-20250605022602415](https://lzc-playground-1301583638.cos.ap-chengdu.myqcloud.com/guidelines/395/20250605030009303.png?imageSlim) 

我们需要把车机里的文件同步到微服里面

所以选择”到右侧文件夹“

![image-20250605022626152](https://lzc-playground-1301583638.cos.ap-chengdu.myqcloud.com/guidelines/395/20250605030009275.png?imageSlim)  

左侧文件填写您行车记录视频的具体存放目录

右侧填写您具体要备份到微服的目录

![image-20250605020159382](https://lzc-playground-1301583638.cos.ap-chengdu.myqcloud.com/guidelines/395/20250605030010151.png?imageSlim) 

##备注部分：部分车机行测记录视频左侧是在SD卡中，选择的时候需要仔细辨认

![image-20250605020425421](https://lzc-playground-1301583638.cos.ap-chengdu.myqcloud.com/guidelines/395/20250605030010098.png?imageSlim) 

左侧与右侧填写完成之后核查清楚就点击保存

![image-20250605020531916](https://lzc-playground-1301583638.cos.ap-chengdu.myqcloud.com/guidelines/395/20250605030010475.png?imageSlim) 

保存完成之后回到主页，就可以进行同步操作了

## 3、同步操作

### 1、手动同步

在您车机有网并连接配置成功之后点击主页配置好的同步按钮进行同步即可

![image-20250605024028403](https://lzc-playground-1301583638.cos.ap-chengdu.myqcloud.com/guidelines/395/20250605030010461.png?imageSlim) 

同步完成会变成绿色

![image-20250605024139696](https://lzc-playground-1301583638.cos.ap-chengdu.myqcloud.com/guidelines/395/20250605030010496.png?imageSlim) 

懒猫微服网盘同步的目录也可以看到内容

![image-20250605024230575](https://lzc-playground-1301583638.cos.ap-chengdu.myqcloud.com/guidelines/395/20250605030010483.png?imageSlim)

![image-20250605024255189](https://lzc-playground-1301583638.cos.ap-chengdu.myqcloud.com/guidelines/395/20250605030011138.png?imageSlim) 

### 2、计划任务同步

**#######重点备注：需要车机待机并且有网#########**

点击主页计划任务——>新增计划任务

![image-20250605024353820](https://lzc-playground-1301583638.cos.ap-chengdu.myqcloud.com/guidelines/395/20250605030011044.png?imageSlim) 

可以给自动同步取一个名字，然后进行相关的间隔时间、连接、通知等规则的编写

![image-20250605024908970](https://lzc-playground-1301583638.cos.ap-chengdu.myqcloud.com/guidelines/395/20250605030011534.png?imageSlim)

规则有间隔时间、连接方式、通知



![image-20250605024832933](https://lzc-playground-1301583638.cos.ap-chengdu.myqcloud.com/guidelines/395/20250605030011747.png?imageSlim)

## 4、扩展

此教程对车机网络有做一定的要求，建议车主设置手动同步或者在一天当中某个长时间使用车机时候进行同步

如果发现同步失败检查方法

1、在web端的cf查看一下隧道是否开启，未开启需要重启一下微服端的cf应用

2、同步需要依靠车机端优质的网络，建议更换网络试试

3、端口转发的是微服局域网IP，请检查微服IP与端口转发工具的IP是否一致，如果长期使用建议固定微服IP
