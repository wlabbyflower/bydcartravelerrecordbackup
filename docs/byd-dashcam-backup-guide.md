# 懒猫微服备份比亚迪行车记录仪指南

本指南用于将比亚迪车机中的行车记录视频，自动或手动同步到懒猫微服网盘（WebDAV）。

## 目标

- 通过公网安全访问微服 WebDAV
- 在车机安装 FolderSync 并配置 WebDAV 账户
- 创建同步任务并执行手动/计划同步

## 前置条件

1. 已有可用的懒猫微服与网盘
2. 已完成 Cloudflare 隧道与端口转发（用于公网访问 WebDAV）
3. 车机可联网，且已允许安装 APK
4. 已准备安装包：[`assets/installers/foldersync.apk`](../assets/installers/foldersync.apk)

## 1. 配置公网访问 WebDAV

请先参考：

- Cloudflared 配置仓库：<https://github.com/wlabbyflower/cloudflared-helper>
- 关键说明：车机端不要开启科学上网，避免与 Cloudflare 连接冲突

配置示例截图：

![cf-config-1](https://lzc-playground-1301583638.cos.ap-chengdu.myqcloud.com/guidelines/395/20250605030007622.png?imageSlim)
![cf-config-2](https://lzc-playground-1301583638.cos.ap-chengdu.myqcloud.com/guidelines/395/20250605030007662.png?imageSlim)

## 2. 安装 FolderSync 到车机

将安装包复制到 U 盘后在车机安装，并在系统设置中授予必要权限。

- 安装包：[`assets/installers/foldersync.apk`](../assets/installers/foldersync.apk)

安装与授权截图：

![install-1](https://lzc-playground-1301583638.cos.ap-chengdu.myqcloud.com/guidelines/395/20250605030007705.png?imageSlim)
![install-2](https://lzc-playground-1301583638.cos.ap-chengdu.myqcloud.com/guidelines/395/20250605030007867.png?imageSlim)

## 3. 在 FolderSync 中添加 WebDAV 账户

打开 FolderSync 后：`用户 -> 添加用户 -> WebDAV`。

![account-entry](https://lzc-playground-1301583638.cos.ap-chengdu.myqcloud.com/guidelines/395/20250605030007689.png?imageSlim)

参数建议：

```text
用户名/密码：懒猫网盘 -> 头像 -> 设置 -> 网络服务 -> WebDAV 用户名与密码
服务器地址：Cloudflare 转出的公网地址（不带 http/https）
端口：443
路径：/dav
高级：全部勾选
身份验证：Basic
```

配置完成后点击测试连接：

![account-test-1](https://lzc-playground-1301583638.cos.ap-chengdu.myqcloud.com/guidelines/395/20250605030008721.png?imageSlim)
![account-test-2](https://lzc-playground-1301583638.cos.ap-chengdu.myqcloud.com/guidelines/395/20250605030008680.png?imageSlim)

## 4. 添加文件夹对（同步任务）

连接测试通过后，点击“添加文件夹对”。

![pair-create](https://lzc-playground-1301583638.cos.ap-chengdu.myqcloud.com/guidelines/395/20250605030008700.png?imageSlim)

配置建议：

1. 设置任务名称
2. 同步引擎建议选择 `V2`
3. 同步方向选择“到右侧文件夹”（车机 -> 微服）
4. 左侧目录填写车机行车记录视频目录
5. 右侧目录填写微服网盘目标目录

截图参考：

![pair-name](https://lzc-playground-1301583638.cos.ap-chengdu.myqcloud.com/guidelines/395/20250605030008696.png?imageSlim)
![pair-engine](https://lzc-playground-1301583638.cos.ap-chengdu.myqcloud.com/guidelines/395/20250605030009303.png?imageSlim)
![pair-direction](https://lzc-playground-1301583638.cos.ap-chengdu.myqcloud.com/guidelines/395/20250605030009275.png?imageSlim)
![pair-path](https://lzc-playground-1301583638.cos.ap-chengdu.myqcloud.com/guidelines/395/20250605030010151.png?imageSlim)

注意：部分车型行车记录视频位于 SD 卡目录，选择源目录时请仔细确认。

![sd-card-note](https://lzc-playground-1301583638.cos.ap-chengdu.myqcloud.com/guidelines/395/20250605030010098.png?imageSlim)

配置完成后保存：

![pair-save](https://lzc-playground-1301583638.cos.ap-chengdu.myqcloud.com/guidelines/395/20250605030010475.png?imageSlim)

## 5. 同步方式

### 5.1 手动同步

在车机联网状态下，点击主页任务的同步按钮执行。

![manual-sync-1](https://lzc-playground-1301583638.cos.ap-chengdu.myqcloud.com/guidelines/395/20250605030010461.png?imageSlim)
![manual-sync-2](https://lzc-playground-1301583638.cos.ap-chengdu.myqcloud.com/guidelines/395/20250605030010496.png?imageSlim)

同步后可在微服网盘目标目录查看文件：

![cloud-result-1](https://lzc-playground-1301583638.cos.ap-chengdu.myqcloud.com/guidelines/395/20250605030010483.png?imageSlim)
![cloud-result-2](https://lzc-playground-1301583638.cos.ap-chengdu.myqcloud.com/guidelines/395/20250605030011138.png?imageSlim)

### 5.2 计划任务同步

重点：计划任务依赖车机待机且网络可用。

路径：`主页 -> 计划任务 -> 新增计划任务`

![schedule-1](https://lzc-playground-1301583638.cos.ap-chengdu.myqcloud.com/guidelines/395/20250605030011044.png?imageSlim)
![schedule-2](https://lzc-playground-1301583638.cos.ap-chengdu.myqcloud.com/guidelines/395/20250605030011534.png?imageSlim)
![schedule-3](https://lzc-playground-1301583638.cos.ap-chengdu.myqcloud.com/guidelines/395/20250605030011747.png?imageSlim)

可根据需求设置：

- 同步间隔
- 网络条件（如仅 Wi-Fi）
- 通知策略

## 6. 常见问题排查

1. 同步失败先检查 Cloudflare 隧道是否在线；若异常，重启微服端 Cloudflare 应用
2. 车机端网络质量不足时，优先更换网络后重试
3. 确认端口转发配置中的微服局域网 IP 与实际 IP 一致；长期使用建议固定微服 IP

## 7. 附件

- 安装包：[`assets/installers/foldersync.apk`](../assets/installers/foldersync.apk)
- 原始说明 PDF：[`assets/references/byd-dashcam-backup.pdf`](../assets/references/byd-dashcam-backup.pdf)
