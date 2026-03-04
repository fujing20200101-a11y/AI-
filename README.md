**命令行推送步骤**
- 安装 Git
  - 访问 https://git-scm.com/downloads 安装后，打开 PowerShell 执行：git --version
- 在 GitHub 创建空仓库
  - 页面里填仓库名，例如 AIjianli，选择 Public/Private，点 Create repository
  - 复制仓库地址，例如：https://github.com/你的账号/AIjianli.git
- 在本机项目根目录执行（注意路径引号）
  - cd "D:\trae智能ai设计\AIjianli"
  - git init
  - git config user.name "你的名字"
  - git config user.email "你的邮箱"
  - git add .
  - git commit -m "chore: init project"
  - git branch -M main
  - git remote add origin https://github.com/你的账号/AIjianli.git
  - git push -u origin main
- 登录与凭证
  - 首次 push 时会弹出登录/令牌框，建议使用 PAT（Personal Access Token）
  - 创建方式：GitHub → Settings → Developer settings → Personal access tokens → Tokens (classic) → 生成一个，勾选 repo 权限，复制后作为“密码”使用

**不要上传的内容（已忽略）**
- 我已添加 [.gitignore](file:///d:/trae智能ai设计/AIjianli/.gitignore)：
  - 忽略 node_modules、dist、logs、.env、.env.local、*.log
- 推送前可检查忽略是否生效：
  - git status --ignored -u

**仓库配置说明（写给使用者的简要）**
- 环境变量（本地创建 .env.local，切勿上传）
  - OPENAI_API_KEY=你的 SiliconFlow Key
  - OPENAI_API_BASE=https://api.siliconflow.cn/v1
  - OPENAI_MODEL=deepseek-ai/DeepSeek-V3
  - CHINESE_AI_PROVIDER=openai
- 开发与运行
  - 后端：node server.js（端口 5000，健康检查 http://localhost:5000/ 返回 ok）
  - 前端：node node_modules/vite/bin/vite.js --port=3000 --host=0.0.0.0
  - 代理：前端通过 /api 代理到 http://localhost:5000（见 [vite.config.ts](file:///d:/trae智能ai设计/AIjianli/vite.config.ts#L22-L27)）
- 生产构建
  - node node_modules/vite/bin/vite.js build
  - 产物位于 [dist](file:///d:/trae智能ai设计/AIjianli/dist)，可部署到静态托管（GitHub Pages/Vercel/Netlify 等）
- 诊断脚本
  - 直连 API 测试：[test_key.js](file:///d:/trae智能ai设计/AIjianli/test_key.js#L1-L45)
  - 后端连通测试：[scripts/test-chat.js](file:///d:/trae智能ai设计/AIjianli/scripts/test-chat.js#L1-L18)
