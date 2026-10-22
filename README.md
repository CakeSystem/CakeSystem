# HashCake

**面向矿场与算力运营团队的一体化 Stratum 矿池代理与管理平台。**

## HashCake 是什么

HashCake 部署在矿机与上游矿池之间，统一处理矿机接入、矿池连接、费用策略和运行监控。通过浏览器即可集中管理代理端口、矿机与矿池线路，并实时查看算力、份额、延迟、告警和服务器状态。

对于不同地区的矿场，可配合 [CakeBox 客户端](https://github.com/hashultra/cakebox) 建立加密隧道，将矿机安全接入 HashCake，降低跨地域接入与线路维护的复杂度。

## 核心能力

| 能力 | 说明 |
| --- | --- |
| 统一接入与管理 | 集中管理代理端口、矿机、矿池线路和 CakeBox 站点，支持配置导入与导出。 |
| 主备矿池线路 | 支持主备上游矿池、断线重连和异常告警，降低线路波动对运行的影响。 |
| 费用策略管理 | 可按端口设置费用矿池与分配比例，并持续对比目标比例和实际比例。 |
| 可视化运营后台 | 实时查看算力、在线与掉线设备、接受与拒绝份额、矿池延迟及服务器资源。 |
| 异地矿场接入 | 配合 CakeBox 建立加密隧道，统一接入和管理不同地区的矿场。 |
| 安全与审计 | 支持 HTTPS、账号权限、安全访问路径、黑名单和管理操作审计。 |
| 可靠安装与升级 | Linux 支持一键安装和下载校验；升级保留原有配置，失败时自动恢复旧版本。 |

## 快速开始

### Linux

在 Linux amd64 服务器上执行：

```bash
bash <(curl -fsSL https://raw.githubusercontent.com/hashultra/hashcake/main/install.sh)
```

如果服务器不能使用 `bash <(...)`，也可以分两步：

```bash
curl -fsSL https://raw.githubusercontent.com/hashultra/hashcake/main/install.sh -o install-hashcake.sh
sudo bash install-hashcake.sh
```

运行要求：Linux amd64、GLIBC 2.31 或更高版本、bash 4 或更高版本、systemd 240 或更高版本、Python 3，并使用 root 权限。一键脚本使用 systemd 管理启停和开机启动；240 是追加日志功能的最低要求，245 可以使用，可选加固项按当前版本启用。缺少依赖时会给出软件包安装提示；二进制不兼容时会保留原始错误。

> [!IMPORTANT]
> 首次登录令牌有效 10 分钟，只用于创建首个管理员账号；账号创建成功后立即失效，之后使用账号与密码登录。

### 国内服务器

无法稳定访问 GitHub 的服务器使用下面的通用管理入口。该命令不绑定当前已安装版本；选择安装或更新时，安装器会自动查找官方最新稳定版，并根据 SHA256SUMS 校验下载文件：
国内镜像的清单缓存可能滞后：安装器会在解析版本时与 GitHub 清单比对，镜像落后时按更新的版本安装，下载仍优先使用国内镜像。

```bash
HASHCAKE_RELEASE_MIRROR_BASE=https://cdn.jsdmirror.com/gh/hashultra/hashcake@main bash <(curl -fsSL https://cdn.jsdmirror.com/gh/hashultra/hashcake@b249a26199a0eb9a54d5729df4ebfe321d198afd/install.sh)
```

### Windows

Windows amd64 程序与 Linux 使用同一正式版本，请从 [Releases 页面](https://github.com/hashultra/hashcake/releases) 下载该版本的 Windows 可执行文件。

## 更新 HashCake

```bash
sudo bash install-hashcake.sh update
```

更新会保留已有 Web 端口、安全访问路径、账号、令牌、配置和状态目录。新版本启动失败时，安装器会自动恢复旧二进制、旧服务文件和原有防火墙状态。

管理菜单按安装与运行、日志与开机启动、后台与配置、维护工具分组，必要功能直接可见。操作结束返回菜单；回车或 0 返回上一级，主菜单中退出。

“15. 修改后台账号密码 / 忘记密码”可以在 SSH 侧改密：知道当前密码时直接修改并复验；忘记密码时在同一入口重置，脚本会先备份状态文件再重建 Owner 账号（现有后台账号会被删除）。

已手动替换程序的离线服务器，把新版安装脚本传入后，选择菜单“5. 重启服务”即可。脚本会自动补齐必要启动设置并检查本地程序，不会联网下载、重新安装或重置账号。选择“3. 启动服务”时，已运行的服务不会被重复启动。

需要切换已发布版本时，选择“17. 安装 / 切换指定版本”，仍执行下载校验与配置预检。手动防火墙及系统连接限制工具分别位于“18. 关闭整机防火墙”和“19. 调整系统连接限制”，执行前显示影响并要求确认。

需要自动化时可显式使用 `bash install-hashcake.sh update` 等命令；完整命令见 `bash install-hashcake.sh --help`。
