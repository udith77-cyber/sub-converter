# 订阅转换 · Sub Converter

纯静态单文件网页：把机场 / 自建订阅链接转换成 Clash、Sing-box、Surge、Quantumult X、Loon 等客户端配置。

转换能力由后端 **subconverter** 服务提供，本页面只负责拼装参数、发起请求、预览与下载。

## 功能

- 粘贴订阅链接（支持多行多条，自动合并）
- 选择目标客户端、ACL4SSR 分流规则（可自定义规则 URL）
- 常用转换选项：emoji / udp / xudp / tls13 / new_name / clash.doh 等
- 生成转换链接，一键复制
- 一键获取并预览转换结果，解析节点列表
- 下载配置文件（YAML / TXT）
- 历史记录保存在本机浏览器（localStorage）

## 本地预览

```bash
cd sub-converter
python3 -m http.server 8080
# 浏览器打开 http://localhost:8080
```

## 部署到 GitHub Pages

1. 在 GitHub 新建仓库（例如 `sub-converter`），不要勾选 README 初始化
2. 推送代码：
   ```bash
   cd sub-converter
   git init
   git add .
   git commit -m "订阅转换页面"
   git branch -M main
   git remote add origin https://github.com/你的用户名/sub-converter.git
   git push -u origin main
   ```
3. 打开仓库 **Settings → Pages**：
   - Source 选择 **Deploy from a branch**
   - Branch 选择 **main**，目录 **/ (root)**，保存
4. 等 1–2 分钟，访问 `https://你的用户名.github.io/sub-converter/` 即可使用

## 关于后端

- 默认使用第三方公共实例 `https://api.v1.mk`，偶发 502 / 无跨域头：
  页面内「一键获取并预览」失败时，请用「新标签页打开」直接访问转换链接。
- 如需稳定服务，可自建 subconverter：
  https://github.com/tindy2013/subconverter
  建好后在页面「转换后端」选择「自定义」填入你的地址。

## 注意

- 订阅链接包含个人 token，请勿把生成的转换链接随意分享。
- 本项目不存储任何订阅信息，历史记录仅保存在你本机浏览器。
