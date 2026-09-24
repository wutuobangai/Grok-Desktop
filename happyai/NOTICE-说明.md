# NOTICE · Happy AI 补 Mac 版说明

## 原项目

- 项目：Grok Desktop（Grok.com 的桌面客户端，支持多标签）
- 原作者：AnRkey（anrkey@gmail.com）
- 原仓库：https://github.com/AnRkey/Grok-Desktop
- 许可证：GNU General Public License v2.0（见仓库根目录 `LICENSE`，原文未改动；Electron 自身许可见 `LICENSE_Electron`）
- 本 fork 基于原仓库 main 分支提交 `6af8d48`（2025-12-20，对应官方最新 Release v1.2.5）

Grok 是 xAI 的产品。本项目与 xAI、原作者均无隶属关系；原作者官方只发布 Windows / Linux 安装包，Mac 版是原仓库 issue #19 用户长期在求的。

## 我们改了什么（全部开源，同样遵守 GPL-2.0）

只加了「能打出 Mac 安装包」这一件事，**应用功能、界面、网址、登录流程一行都没改，没加任何广告或弹窗**：

1. `package.json`
   - `scripts` 新增 `build-mac`（electron-builder 打 dmg，arm64 + x64）
   - `build` 新增 `mac`（target dmg、分类 productivity、图标用仓库原有的 `build-resources/icons/512x512.png`）和 `dmg`（文件名）两段配置
2. `.github/workflows/happyai-build.yml`：云端构建 Mac dmg + 在一次性虚拟机里启动截屏；Windows 直接测试原作者官方安装包（不自己编译 Windows 版）
3. `happyai/NOTICE-说明.md`：本文件
4. `README.md`：顶部加了一段中文下载说明和维护者信息，原 README 全文保留在下面

`src/`、`index.html` 等应用代码与原作者完全相同。自动更新：原程序本身没有自动更新功能，我们也没有加。

## Mac 版怎么打开（未签名）

我们没有苹果开发者证书，Mac 版是**未签名**的，第一次打开会被系统拦一下，属于正常现象：

1. 下载对应芯片的 dmg：M1/M2/M3/M4 等苹果芯片选 `mac-arm64`，老款 Intel 芯片选 `mac-x64`
2. 双击 dmg，把「Grok Desktop」拖进「应用程序」
3. 双击打开，系统提示「无法验证开发者」→ 点「完成」
4. 打开 **系统设置 → 隐私与安全性**，往下拉，看到「已阻止使用 Grok Desktop」→ 点 **「仍要打开」** → 输入开机密码
5. 之后就能正常双击打开了

如果提示「已损坏，无法打开」：打开「终端」，粘贴下面一行回车（输入开机密码时屏幕不显示，照打回车即可），再双击打开：

```
sudo xattr -cr "/Applications/Grok Desktop.app"
```

## 已知问题（原程序本身的，非我们引入）

- 原仓库 issue #26：部分用户登录时「Verify you are human」人机验证反复出现、登不进去。遇到这种情况，直接用浏览器打开 https://grok.com 登录效果一样。
- 原程序关闭了菜单栏，Mac 上 ⌘C / ⌘V 复制粘贴等快捷键可能不可用（原程序快捷键按 Windows/Linux 的 Ctrl 设计）。

## 维护者

Happy AI · 阿浩（抖音「跟着阿浩玩Ai」）· 官网 https://wutuobangai.top
