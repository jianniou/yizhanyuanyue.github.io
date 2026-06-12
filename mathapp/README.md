# 数学闯关 · 静态合规站点

为「数学闯关」App 准备的静态网页,可直接用于 App Store 审核要求的：
- **隐私政策(Privacy Policy)URL**
- **使用条款(Terms of Use / EULA)URL**
- **技术支持(Support)URL**

## 文件结构

```
web/
├── index.html      # 应用主页(产品介绍 + 订阅方案)
├── privacy.html    # 隐私政策
├── terms.html      # 使用条款
├── support.html    # 技术支持 + FAQ
└── style.css       # 共享样式
```

## 开发者信息

- 开发者：QiYuan
- 联系邮箱：410869924@qq.com

如需更改，请同步修改 `privacy.html` / `terms.html` / `support.html` 中对应位置。

## 本地预览

```bash
cd web
python3 -m http.server 8000
# 打开 http://localhost:8000
```

## 部署方式(任选其一)

### 1. GitHub Pages(推荐,免费)
1. 把 `web/` 目录推到任意 GitHub 仓库;
2. Settings → Pages → Source 选 `main` 分支 / `web` 目录;
3. 几分钟后即可通过 `https://<你的用户名>.github.io/<仓库名>/` 访问;
4. 把对应 URL 填入 App Store Connect 的隐私政策 / 服务条款 / 支持地址。

### 2. Vercel / Netlify
直接拖拽 `web/` 目录上传,会自动分配域名。

### 3. 自有服务器
把 `web/` 内容上传到任意 HTTPS 静态文件目录即可。

## 合规性说明

页面内容已根据当前工程实际情况撰写:
- ✅ 工程为**纯本地存储**(SwiftData + Keychain),无服务器、无网络请求;
- ✅ 仅集成 **Apple StoreKit 2**,无任何第三方分析 / 广告 / 统计 SDK;
- ✅ 应用内购价格 ¥3 / 月、¥36 / 年,与 `MathQuestApp.storekit` 配置一致;
- ✅ 试用期 10 天,与 `SubscriptionState.swift` 中 `byAdding: .day, value: 10` 一致;
- ✅ 强调**儿童隐私保护**,符合《未成年人保护法》、《儿童个人信息网络保护规定》、COPPA;
- ✅ 自动续期条款符合 App Store 审核 3.1.2(a) 要求(扣款时机、续期价格、取消方式)。

## 后续维护

- 当订阅价格调整时,需同步更新 `index.html` / `terms.html` 的价格表;
- 若未来引入 iCloud 同步、第三方分析 SDK 等,**必须**修改 `privacy.html` 第 3 / 4 节;
- 政策变更时记得更新页面顶部的"最后更新"日期。
