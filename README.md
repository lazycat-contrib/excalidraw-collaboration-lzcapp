# Excalidraw Collaboration for LazyCat

将 [alswl/excalidraw-collaboration](https://github.com/alswl/excalidraw-collaboration) 打包为懒猫微服 LPK v2 应用，提供白板、场景存储和实时多人协作。

## 服务结构

- `/`：Excalidraw 前端
- `/storage/`：场景与文件存储 API
- `/socket.io/`：实时协作 WebSocket
- 存储后端使用 SQLite，数据保存在 `/lzcapp/var/storage`

三个运行镜像均通过 `docker.1ms.run` mirror 交付，并要求 mirror 与上游 `linux/amd64` 镜像 digest 一致。应用版本跟随 `alswl/excalidraw` 的 `v<version>-fork-b<build>` 标签。

## 本地构建

```sh
lzc-cli project release -o .lazycat-build/excalidraw-collaboration.lpk
lzc-cli lpk info .lazycat-build/excalidraw-collaboration.lpk
```

## 自动发布

`.github/workflows/lazycat.yml` 每日检查镜像，也支持手动触发和 `v*` 标签触发。自动化会创建版本化 GitHub Release Asset，并且只发布到喵喵商店；官方商店保持关闭。

仓库或组织需要向本仓库授权以下 GitHub Secrets：

- `APPSTORE_URL`
- `APPSTORE_TOKEN`
- `APP_ID`（可选）
- `PRIVATE_STORE_GROUP_CODES`（可选）

## 上游与许可

- 上游软件仓库：<https://github.com/alswl/excalidraw-collaboration>
- 本打包仓库沿用上游 MIT License。
