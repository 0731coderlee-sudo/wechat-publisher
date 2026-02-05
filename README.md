# wechat-publisher

**一键发布 Markdown 到微信公众号草稿箱 🚀**

## 🎯 快速开始

### 1. 发布测试文章

```bash
cd /Users/leebot/.openclaw/workspace/wechat-publisher

# 方式 1: 使用脚本（推荐）
./scripts/publish.sh test-article.md

# 方式 2: 直接使用 wenyan
wenyan publish -f test-article.md -t lapis -h solarized-light
```

### 2. 查看草稿箱

前往微信公众号后台：https://mp.weixin.qq.com/

草稿箱 → 查看刚发布的文章 → 审核 → 发布

---

## 📝 使用方法

### 准备 Markdown 文件

```markdown
---
title: 文章标题（必填！）
cover: https://example.com/cover.jpg  # 封面图（必填！）
---

# 正文开始

你的内容...
```

**⚠️ 重要：** title 和 cover **都是必填**，缺一不可！

### 发布文章

```bash
./scripts/publish.sh your-article.md [theme] [highlight]
```

**示例：**
```bash
# 使用默认主题
./scripts/publish.sh article.md

# 指定主题
./scripts/publish.sh article.md lapis

# 指定主题和代码高亮
./scripts/publish.sh article.md lapis solarized-light
```

---

## 🎨 主题选项

查看所有可用主题：
```bash
wenyan theme -l
```

**推荐组合：**
- `lapis` + `solarized-light` - 优雅蓝色（推荐）
- `phycat` + `github` - 简洁现代
- `default` + `xcode` - 经典风格

详见：[references/themes.md](references/themes.md)

---

## 🔧 配置

### 环境变量

**方式 1: 使用 setup.sh**
```bash
source ./scripts/setup.sh
```

**方式 2: 手动设置**
```bash
export WECHAT_APP_ID=your_wechat_app_id
export WECHAT_APP_SECRET=your_wechat_app_secret
```

**方式 3: 永久设置**

编辑 `~/.zshrc`：
```bash
echo 'export WECHAT_APP_ID=your_wechat_app_id' >> ~/.zshrc
echo 'export WECHAT_APP_SECRET=your_wechat_app_secret' >> ~/.zshrc
source ~/.zshrc
```

### IP 白名单

**获取你的 IP：**
```bash
curl ifconfig.me
```

**添加到白名单：**
1. 登录：https://mp.weixin.qq.com/
2. 开发 → 基本配置 → IP 白名单
3. 添加你的 IP 地址

---

## 📚 文档

- **使用指南：** [SKILL.md](SKILL.md)
- **主题列表：** [references/themes.md](references/themes.md)
- **故障排查：** [references/troubleshooting.md](references/troubleshooting.md)

---

## 🛠️ 依赖

- **Node.js** >= 14.0.0
- **wenyan-cli** (自动安装)

---

## 💡 在 OpenClaw 中使用

只需告诉 leezy：

> "帮我发布这篇文章到微信公众号" + 提供 Markdown 文件路径

leezy 会自动调用这个 skill！

---

## 📦 文件结构

```
wechat-publisher/
├── SKILL.md                    # 完整文档
├── README.md                   # 快速开始
├── test-article.md             # 测试文章
├── scripts/
│   ├── publish.sh              # 发布脚本
│   └── setup.sh                # 环境变量设置
└── references/
    ├── themes.md               # 主题列表
    └── troubleshooting.md      # 故障排查
```

---

## 🎉 特性

- ✅ 一键发布到草稿箱
- ✅ 自动上传图片到微信图床
- ✅ 多主题支持（代码高亮、Mac 风格）
- ✅ 本地/网络图片都支持
- ✅ 完整的错误提示和帮助

---

## 📖 示例

### 基本使用
```bash
./scripts/publish.sh article.md
```

### 指定主题
```bash
./scripts/publish.sh article.md lapis solarized-light
```

### 查看帮助
```bash
./scripts/publish.sh --help
wenyan --help
```

---

## 🐛 遇到问题？

查看：[references/troubleshooting.md](references/troubleshooting.md)

常见问题：
- IP 不在白名单 → 添加到公众号后台
- wenyan 未安装 → `npm install -g @wenyan-md/cli`
- 环境变量未设置 → `source ./scripts/setup.sh`

---

## 📄 License

Apache License 2.0 (继承自 wenyan-cli)

---

**Powered by [wenyan-cli](https://github.com/caol64/wenyan-cli)**
