# 占卜盘 · 固定入口

`https://bietou123.github.io/zhanbu-go/` 是「占卜盘」（zhanbu-v2）的**固定入口**。

> 注意：`https://bietou123.github.io/zhanbu/` 是另一个项目——八字排盘网站（[bietou123/zhanbu](https://github.com/bietou123/zhanbu)），两者不是同一个应用。

应用通过 cloudflared quick tunnel 暴露，隧道每次重启都会换地址，所以这里只放一个跳转页，由 NAS 定时脚本自动更新：

- 脚本：`update_redirect.py --job zhanbu`（仅标准库）
- 逻辑：`docker logs zhanbu-tunnel` 里取最新的 `*.trycloudflare.com` 地址 → 与上次对比 → 变了就重渲染 `index.html` 并推送
- 跳转目标不在本仓库里，本仓库只有这个跳转页和说明

## 页面状态

- **正在跳转**：说明隧道地址有效
- **固定入口已就绪，但后台隧道还没上报地址**：NAS 上的脚本还没跑过，或容器刚重启还没拿到新地址

## 源码

应用源码：[bietou123/zhanbu-v2](https://github.com/bietou123/zhanbu-v2)

## 许可

MIT
