# GitHub Pages 部署指南

## 当前状态
✅ GitHub Actions workflow 已配置
✅ 所有文件已 commit 到本地 main 分支
⏳ 等待推送到 GitHub

## 快速部署步骤

### 步骤 1：推送代码到 GitHub

在你的本地机器上执行：

```bash
cd /data/.openclaw/workspace-dev/my-daily-memory
git push -u origin main
```

如果需要认证，使用以下方式之一：

#### 方式 A：Personal Access Token (推荐)
1. 访问 https://github.com/settings/tokens
2. 点击 "Generate new token (classic)"
3. 勾选 `repo` 权限
4. 生成 token 并复制
5. 推送时使用：
   ```bash
   git push https://YOUR_TOKEN@github.com/ericlinyi1/my-daily-memory.git main
   ```

#### 方式 B：SSH Key
```bash
# 如果你已配置 SSH key
git remote set-url origin git@github.com:ericlinyi1/my-daily-memory.git
git push -u origin main
```

### 步骤 2：启用 GitHub Pages

推送成功后：

1. 访问仓库设置页面：
   ```
   https://github.com/ericlinyi1/my-daily-memory/settings/pages
   ```

2. 在 **Source** 部分：
   - 选择 "GitHub Actions"（而不是 "Deploy from a branch"）

3. 点击 **Save**

### 步骤 3：等待部署

- GitHub Actions 会自动运行
- 查看进度：https://github.com/ericlinyi1/my-daily-memory/actions
- 首次部署约需 1-3 分钟

### 步骤 4：验证部署

部署完成后，你的隐私政策将发布在：

```
https://ericlinyi1.github.io/my-daily-memory/web/app-store-privacy-policy.html
```

**这就是你在 App Store Connect 填写的 Privacy Policy URL！**

## 测试隐私政策页面

```bash
# 测试 URL 可访问性
curl -I https://ericlinyi1.github.io/my-daily-memory/web/app-store-privacy-policy.html

# 应该返回 HTTP/2 200
```

在浏览器中打开：
- Landing Page: https://ericlinyi1.github.io/my-daily-memory/web/index.html
- Privacy Policy: https://ericlinyi1.github.io/my-daily-memory/web/app-store-privacy-policy.html

## 自动部署流程

一旦设置完成，之后的更新流程：

```bash
# 1. 修改文件
vim web/app-store-privacy-policy.html

# 2. Commit
git add .
git commit -m "Update privacy policy"

# 3. Push（自动触发部署）
git push origin main
```

GitHub Actions 会在每次推送到 main 分支时自动重新部署。

## 故障排查

### 如果 Actions 运行失败

1. 检查 Actions 权限：
   - 仓库设置 → Actions → General
   - "Workflow permissions" 选择 "Read and write permissions"
   - 勾选 "Allow GitHub Actions to create and approve pull requests"

2. 重新运行 workflow：
   - 访问 https://github.com/ericlinyi1/my-daily-memory/actions
   - 点击失败的 workflow
   - 点击 "Re-run all jobs"

### 如果 Pages 未启用

确保在仓库设置中：
- Settings → Pages → Source → **GitHub Actions**

### 如果 404 错误

- 确认文件路径正确：`web/app-store-privacy-policy.html`
- 等待 2-5 分钟让 DNS 传播
- 清除浏览器缓存

## App Store Connect 配置

在提交 iOS app 时，填写：

**Privacy Policy URL:**
```
https://ericlinyi1.github.io/my-daily-memory/web/app-store-privacy-policy.html
```

**App Privacy 问卷:**
- Data Collection: No
- Tracking: No
- Data Linked to You: None

## 自定义域名（可选）

如果你想使用自定义域名（如 `mydailymemory.app`）：

1. 购买域名
2. 在域名 DNS 设置中添加：
   ```
   Type: CNAME
   Name: www
   Value: ericlinyi1.github.io
   ```
3. 在仓库中创建 `CNAME` 文件：
   ```bash
   echo "mydailymemory.app" > CNAME
   git add CNAME
   git commit -m "Add custom domain"
   git push
   ```
4. 在 GitHub 仓库设置 → Pages → Custom domain 中输入域名

## 备用方案：手动下载并部署

如果无法推送，可以：

1. 从本地复制整个项目文件夹
2. 在 GitHub 网页上：
   - 访问 https://github.com/ericlinyi1/my-daily-memory
   - 点击 "Add file" → "Upload files"
   - 拖拽所有文件上传
   - Commit changes
3. 按上述步骤启用 GitHub Pages

---

**当前提交历史：**
```
d6d9eb1 Add GitHub Actions workflow for automatic Pages deployment
f65ce2c Add App Store-ready privacy policy page
bff211d docs: add comprehensive Product Requirements Document (PRD)
ceed8ca Initial commit: My Daily Memory project setup
```

所有文件已准备就绪，只需推送即可！
