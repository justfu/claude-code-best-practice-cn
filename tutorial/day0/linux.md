# Linux 安装指南

[返回第 0 天](README.md)

## 前提条件

你需要 **Node.js v18 或更高版本** 和 **npm**。

## 第一步：安装 Node.js

### 选项 A：通过 nodejs.org 下载页面配合 fnm（推荐）

**fnm**（Fast Node Manager）是 Node.js 官方推荐的工具。它速度快、轻量级，并且可以在需要时轻松切换 Node 版本。

1. 打开浏览器，访问 [nodejs.org/en/download](https://nodejs.org/en/download)。

2. 你会看到一排下拉菜单，显示：**"Get Node.js® vXX.XX.X (LTS) for __ using __ with __"**。按如下设置：

   | 下拉菜单 | 选择 |
   |----------|--------|
   | 版本 | **vXX.XX.X (LTS)** — 保持默认 LTS 版本，不要更改 |
   | 操作系统 | **Linux** |
   | 包管理器 | **fnm**（在"Recommended (Official)"下） |
   | 包格式 | **npm** — 保持默认 |

3. 页面会显示需要运行的命令。打开终端并复制粘贴。命令大概如下：

   ```bash
   # 第一步 — 安装 fnm
   curl -fsSL https://fnm.vercel.app/install | bash

   # 第二步 — 重启终端或重新加载 shell 配置
   source ~/.bashrc   # 或: source ~/.zshrc (如果你使用 zsh)

   # 第三步 — 安装 Node.js
   fnm install 24   # 页面会显示确切的版本号
   ```

   > 版本号可能与上面不同 — 始终使用网站上显示的版本。

4. **关闭并重新打开终端**（或运行上面的 `source` 命令），这样 `fnm`、`node` 和 `npm` 就可以使用了。

> **为什么用 fnm？** 它在 Node.js 下载页面的"推荐（官方）"类别中。和 nvm 一样，它将 Node 安装在你的主目录中，因此你永远不需要使用 `sudo` 来进行 npm 全局安装 — 但 fnm 明显更快（用 Rust 编写），并且在 Windows、macOS 和 Linux 上的工作方式完全相同。

### 选项 B：使用你的发行版的包管理器

这种方式更快，但可能安装较旧版本的 Node.js。**安装后检查版本** — 如果低于 v18，请改用选项 A。

**Ubuntu / Debian：**

```bash
sudo apt update
sudo apt install -y nodejs npm

# 检查版本
node --version   # 必须是 v18 或更高
```

**Fedora：**

```bash
sudo dnf install -y nodejs npm
```

**Arch Linux：**

```bash
sudo pacman -S nodejs npm
```

### 选项 C：NodeSource（通过 apt 安装最新 LTS，无需 nvm）

适用于 Ubuntu/Debian 用户，想安装最新 LTS 但不想使用 nvm：

```bash
curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo -E bash -
sudo apt install -y nodejs
```

## 第二步：验证 Node.js

```bash
node --version
npm --version
```

两者都应该显示版本号。`node --version` 必须显示 v18.x 或更高。

## 第三步：安装 Claude Code

```bash
npm install -g @anthropic-ai/claude-code
```

> **权限报错？**
> - 如果你使用了 **fnm** 或 **nvm**：不应该出现此问题。检查它是否激活（`which node` 应该指向你主目录中的路径，而不是 `/usr/...`）。
> - 如果你使用了系统安装：要么使用 `sudo npm install -g @anthropic-ai/claude-code`，要么修复 npm 的全局目录权限：
>   ```bash
>   mkdir -p ~/.npm-global
>   npm config set prefix '~/.npm-global'
>   echo 'export PATH=~/.npm-global/bin:$PATH' >> ~/.bashrc
>   source ~/.bashrc
>   ```

## 第四步：验证 Claude Code

```bash
claude --version
```

你应该能看到 Claude Code 的版本号。现在回到 [README.md](README.md) 进行身份验证设置。

---

## 注意事项

- **WSL（Windows 子系统 Linux）：** 本指南也适用于 WSL 内部。只需在 WSL 终端中按照这些步骤操作即可。
- **PATH 问题：** 如果安装后找不到 `claude`，请确保 npm 的全局 bin 目录在你的 PATH 中。运行 `npm config get prefix` — 该路径的 `bin/` 子目录需要在你的 PATH 中。
