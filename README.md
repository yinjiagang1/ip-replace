# ♻️ 节点 IP / 端口 / 备注 批量替换工具

这是一个基于 Web 的轻量级工具，用于批量修改 **Vmess**、**Vless** 和 **Trojan** 节点的 IP 地址、端口、备注名以及 ProxyIP 参数。

它完全运行在浏览器端（纯前端逻辑），安全快速，支持 CIDR IP 段生成。

![License](https://img.shields.io/badge/license-MIT-blue)

## ✨ 主要功能

- **多协议支持**：支持 Vmess (Base64)、Vless (URL Scheme)、Trojan (URL Scheme)。
- **批量处理**：支持一次性输入多个 IP 或 IP 段。
- **CIDR 解析**：支持输入 CIDR 格式（如 `192.168.1.0/24`），自动生成该网段下的所有 IP。
- **自定义端口与备注**：
  - 格式支持：`IP:端口#备注`
  - 示例：`1.1.1.1:8443#优化节点`
- **ProxyIP 模式**：专为 Cloudflare Workers / Edge Tunnel 脚本设计，可批量替换 URL 中的 `&proxyip=` 参数。
- **隐私安全**：所有计算在本地浏览器完成，不会上传任何节点信息到服务器。

## 📂 文件说明

本项目包含两种部署方式的源代码：

1.  **`_worker.js`**：用于部署在 **Cloudflare Workers**（包含服务端逻辑和内嵌 HTML）。
2.  **`index.html`**：用于部署在 **Cloudflare Pages**、GitHub Pages 或任何静态服务器。

---

## 🚀 部署教程

你可以根据喜好选择以下任意一种方式部署。

### 方式一：部署到 Cloudflare Workers (推荐)

这种方式不需要 GitHub 仓库，直接在 Cloudflare 后台粘贴代码即可，自带免费域名。

1.  登录 [Cloudflare Dashboard](https://dash.cloudflare.com/)。
2.  进入 **Workers & Pages** -> **Overview**。
3.  点击 **Create Application** -> **Create Worker**。
4.  命名你的 Worker（例如 `ip-tools`），点击 **Deploy**。
5.  点击 **Edit code**。
6.  清空编辑器中的现有代码。
7.  将本项目中的 `_worker.js` 文件的**全部内容**复制并粘贴进去。
8.  点击右上角的 **Save and Deploy**。
9.  访问 Worker 分配的域名即可使用。

### 方式二：部署到 Cloudflare Pages (静态托管)

如果你有自己的域名或者喜欢静态托管方式。

1.  将本项目中的 `index.html` 文件下载到本地电脑。
2.  登录 [Cloudflare Dashboard](https://dash.cloudflare.com/)。
3.  进入 **Workers & Pages** -> **Overview**。
4.  点击 **Create Application** -> **Pages** 标签页 -> **Upload assets**。
5.  输入项目名称（例如 `ip-tools-web`），点击 **Create project**。
6.  将包含 `index.html` 的文件夹（或者直接拖拽文件）上传。
7.  点击 **Deploy site**。
8.  访问 Pages 分配的域名即可使用。

> **提示**：`index.html` 也可以直接双击在本地浏览器打开使用，或者部署到 GitHub Pages、Vercel、Netlify 等平台。

---

## 📖 使用指南

### 1. 输入格式

在 "IP / 端口 / 列表" 输入框中，支持以下几种格式（每行一条，或用逗号分隔）：

- **仅 IP**：