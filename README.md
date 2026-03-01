# bydcartravelerrecordbackup

比亚迪车机行车记录视频备份到懒猫微服网盘的文档与附件仓库。

## 快速入口

- 主教程：[`docs/byd-dashcam-backup-guide.md`](docs/byd-dashcam-backup-guide.md)
- 文档索引：[`docs/README.md`](docs/README.md)
- 安装包：[`assets/installers/foldersync.apk`](assets/installers/foldersync.apk)
- 原始 PDF：[`assets/references/byd-dashcam-backup.pdf`](assets/references/byd-dashcam-backup.pdf)

## 目录结构

```text
.
├── README.md
├── docs
│   ├── README.md
│   └── byd-dashcam-backup-guide.md
└── assets
    ├── installers
    │   └── foldersync.apk
    └── references
        └── byd-dashcam-backup.pdf
```

## 适用条件

- 已有懒猫微服与网盘
- 已配置 Cloudflare 隧道与端口转发（对外访问 WebDAV）
- 车机可联网并允许安装 APK

## 相关参考

- Cloudflared 配置参考：<https://github.com/wlabbyflower/cloudflared-helper>
