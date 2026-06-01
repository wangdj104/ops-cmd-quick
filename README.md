# 运维命令速查

Linux / Kubernetes / Docker 等运维命令速查表，支持搜索、分类、一键复制；附带 **AI 命令助手**（自然语言生成可复制命令）。

## 在线访问（GitHub Pages）

启用 Pages 后访问：

**https://wangdj104.github.io/ops-cmd-quick/**

（仓库名或用户名变更时，地址会变为 `https://<你的用户名>.github.io/<仓库名>/`）

## 发布到 GitHub Pages（一次性配置）

### 1. 推送代码到 GitHub

仓库已关联：`https://github.com/wangdj104/ops-cmd-quick.git`

在本地项目目录执行（**不要**提交含 Key 的 `ai-config.local.js`）：

```bash
cd e:\自研项目\ops-cmd-quick

git status
# 确认 ai-config.local.js 不在待提交列表中

git add index.html README.md .gitignore .nojekyll ai-config.local.js.example
git commit -m "docs: 添加 GitHub Pages 部署说明"
git push origin main
```

若 `git status` 里出现 `ai-config.local.js`，说明被误跟踪，执行：

```bash
git rm --cached ai-config.local.js
```

### 2. 在 GitHub 开启 Pages

1. 打开 https://github.com/wangdj104/ops-cmd-quick/settings/pages  
2. **Build and deployment** → **Source** 选 **Deploy from a branch**  
3. **Branch** 选 `main`，文件夹选 **`/ (root)`**  
4. 点 **Save**  
5. 等 1～3 分钟，页面顶部会显示绿色访问地址

根目录已有 `index.html`，Pages 会自动把它作为站点首页。

### 3. 验证

浏览器打开 Pages 地址，能搜索、能复制命令即可。  
点顶栏 **「✦ AI 命令」** 测试 AI（见下文 Key 说明）。

## AI 功能（线上必读）

- **不要把 API Key 写进仓库或 `index.html`**，否则任何人都能在 GitHub 上看到并盗用。  
- 线上每位使用者在自己的浏览器里：**「✦ AI 命令」→ API 配置 → 填写 DashScope Key → 保存配置到本机**（存在 `localStorage`，仅本机）。  
- 默认接口与模型已预填，一般只需填 Key。  
- 本地开发可选用 `ai-config.local.js`（已 `.gitignore`），复制 `ai-config.local.js.example` 后改名填写。

若浏览器提示跨域（CORS）失败，多为接口不允许从 `github.io` 域名直连，需改用 [阿里云文档](https://help.aliyun.com/zh/model-studio/) 允许的调用方式，或自建同源代理（勿把 Key 放在代理的公开前端里）。

## 仓库文件说明

| 文件 | 说明 |
|------|------|
| `index.html` | 站点全部功能（单文件） |
| `.nojekyll` | 关闭 Jekyll，避免 Pages 误处理 |
| `ai-config.local.js.example` | 本地 Key 配置模板 |
| `ai-config.local.js` | 仅本机，**勿提交** |

## 更新站点

改完 `index.html` 后 `git push origin main`，Pages 会自动重新部署，通常 1～2 分钟生效。

## 自定义域名（可选）

Settings → Pages → **Custom domain** 填写域名，并按提示在 DNS 添加 CNAME 记录。
