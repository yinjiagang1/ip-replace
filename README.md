# ♻️ 节点 IP / 端口 / 备注 批量替换工具
![后台页面](./img.png)

这是一个基于 Web 的轻量级工具，用于批量修改 **Vmess**、**Vless** 和 **Trojan** 节点的 IP 地址、端口、备注名以及 ProxyIP 参数。

它完全运行在浏览器端（纯前端逻辑），安全快速，支持 CIDR IP 段生成。
>**提示**：`ip-replacement.html` 也可以直接双击在本地浏览器打开使用 **（推荐）**，或者部署到 GitHub Pages、Vercel、Netlify 等平台。

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
2.  **`ip-replacement.html`**：本地双击运行 或 部署在 **Cloudflare Pages**、GitHub Pages 等任何静态服务器。

---

## 🚀 部署教程

你可以根据喜好选择以下任意一种方式部署。

### 方式一：部署到 Cloudflare Workers

1.  登录 [Cloudflare](https://dash.cloudflare.com/)。    
2.  进入 **计算和 AI** -> **Workers & Pages** -> **创建应用程序**，或者**账户主页** -> **开发人员平台** -> **创建应用程序**。  
3.  点击 **从 Hello World!开始。      
4.  命名你的 Worker（例如 `ip-tools`），点击 **部署**。
5.  点击 **编辑代码**。    
6.  清空编辑器中的现有代码。
7.  将本项目中的 `_worker.js` 文件的**全部内容**复制并粘贴进去。
8.  点击右上角的 **部署**。  
9.  Worker 分配的域名无法访问，需要绑定自定义域名。

### 方式二：部署到 Cloudflare Pages    

如果你有自己的域名或者喜欢静态托管方式。

1.  将本项目中的 `ip-replacement.html` 文件下载到本地电脑。
2.  登录 [Cloudflare](https://dash.cloudflare.com/)。  
3.  进入 **计算和 AI** -> **Workers & Pages** -> **创建应用程序**，或者**账户主页** -> **开发人员平台** -> **创建应用程序**。    
4.  点击Looking to deploy Pages?后面的 **Get started** -> 拖放文件**开始使用**。    
5.  输入项目名称（例如 `ip-tools-web`），点击 **创建项目**。
6.  将包含 `ip-replacement.html` 的文件夹（或者直接拖拽文件）上传。
7.  点击 **部署站点**。    
8.  访问 Pages 分配的域名即可使用。
---
