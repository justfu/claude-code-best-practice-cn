# 第 0 天 — Claude Code 安装指南

本指南将带你完成在本地机器上安装 Claude Code 并进行身份验证，让你可以开始使用它。

## 第一步：安装 Claude Code

选择你的操作系统：

| 操作系统 | 安装指南 |
|----|-------|
| Windows | [windows.md](windows.md) |
| Linux | [linux.md](linux.md) |
| macOS | [mac.md](mac.md) |

按照对应操作系统的指南操作，然后回到这里进行身份验证。

---

## 第二步：验证安装

按照操作系统特定的指南完成后，确认一切正常：

```bash
node --version    # 应该显示 v18.x 或更高版本
claude --version  # 应该显示已安装的 Claude Code 版本
```

---

## 第三步：登录

<img src="assets/login.png" alt="Claude Code 登录界面" width="50%">

在终端中运行 `claude`。首次启动时，它会要求你选择登录方式。

### 方式一：订阅（Claude Pro / Max）

- 选择 **Claude.ai 账户**
- 浏览器会打开 — 登录并授权
- 返回终端，你就已经登录了

### 方式二 a：API Key（团队邀请）

你的团队管理员从 Anthropic 控制台邀请你。

- 你会收到一封**邀请邮件** — 接受邀请并创建你的 Anthropic 账户
- 在终端中运行 `claude`
- 选择 **Anthropic API Key**
- 你的 Key 会在控制台中**自动生成** — 无需手动设置
- Claude Code 立即可用

### 方式二 b：API Key（你已有 Key）

如果有人通过 Slack、邮件等方式分享了 Key 给你，或者你自己创建了 Key：

- 在终端中运行 `claude`
- 选择 **Anthropic API Key**
- 粘贴你的 Key（以 `sk-ant-` 开头）
- Key 会**永久保存** — 你不会被再次要求输入

---
