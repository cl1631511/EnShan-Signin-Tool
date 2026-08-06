# EnShan-Signin-Tool

恩山论坛每日签到脚本，青龙面板专用。

2026年8月 实测可用

> 项目部分代码来源于 [FunSeason/enshan](https://github.com/FunSeason/enshan)。

## ✨ 功能特性

- **🛡️ 强力过盾**：使用浏览器原生环境模拟操作，绕过 Cloudflare / 顶象 / 云盾等防火墙拦截。
- **🍪 Cookie 自愈**：检测 Cookie 是否有效，若失效可触发浏览器验证并回写 `config.json`。
- **🌍 双语适配**：兼容英文页面与论坛翻译插件，稳定抓取签到数据。
- **♻️ 进程自愈**：执行前清理残留浏览器进程，避免任务被僵尸进程影响。
- **⏰ 随机延迟**：默认启用随机等待，模拟真实用户行为，降低风控风险。
- **📲 青龙通知**：直接调用青龙面板发送签到结果，无需额外配置。

## 🚀 青龙面板运行指南

### 1. 导入仓库

在青龙面板中添加订阅：

```text
名称：EnShanSigninTool
链接：https://github.com/quan-ge/EnShan-Signin-Tool.git
白名单：enshan_sign.py
定时规则：2 2 28 * *
```

网络不佳请科学上网 或改为：

```text
https://fgp.120322.dpdns.org/https://github.com/quan-ge/EnShan-Signin-Tool.git
```

### 2. 安装依赖

打开青龙面板的“依赖管理”

安装Python3依赖：

- `DrissionPage`
- `requests`

安装Linux依赖：

- `chromium`
- `chromium-chromedriver`

### 3. 配置变量

请在青龙面板的环境变量页面配置，参考下方[变量说明](#%EF%B8%8F-变量说明)

###  ~~方式二：本地运行~~ (新版已弃用，不提供任何维护，请安装青龙面板或使用其他项目)

~~1. 安装 Python 3.8+。
2. 安装库：`pip install DrissionPage requests`。
3. 安装 Chrome 或 Edge 浏览器。
4. 修改代码中的浏览器路径配置（如果脚本找不到浏览器的话）。
5. 运行：`python enshan_sign.py`。~~

## ⚙️ 变量说明

> 所有以 `EST_` 开头的环境变量都会同步到 `config.json`，以环境变量为准。

| 参数名                   | 类型   | 默认值 | 说明                                                   |
| ------------------------ | ------ | ------ | ------------------------------------------------------ |
| `EST_USER_UID`           | 字符串 | 无     | 恩山论坛 UID，登录后个人主页地址栏 `uid=` 后面的数字。 |
| `EST_cookie`             | 字符串 | 无     | 登录后浏览器 Cookie，用于模拟登录状态。                |
| `EST_ENABLE_RANDOM_WAIT` | 字符串 | `true` | 是否启用随机延迟启动；仅支持 `true` 或 `false`。       |

### 参数获取方式

- **EST_USER_UID**：登录恩山论坛 -> 点击右上角头像 -> 地址栏 `uid=` 后面的数字。
- **EST_cookie**：
  1. 浏览器登录恩山论坛。
  2. 按 `F12` 打开开发者工具，进入 `Network`。
  3. 刷新页面，选择一个请求（如 `forum.php`）。
  4. 在 `Headers` 中找到 `Cookie:`，复制其后的全部字符串。

## ⚠️ 免责声明

- 本脚本仅供学习交流使用，不可用于商业用途。
- 使用脚本产生的任何后果由使用者自行承担。
- 请遵守恩山无线论坛相关规定，合理使用自动化工具。
