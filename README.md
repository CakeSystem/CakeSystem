# HashCake

**自托管多币种 Stratum 矿池代理（minerproxy）：矿机接入、矿池中转、费用策略和算力监控集中到一个 Web 后台。**

HashCake 部署在矿机与上游矿池之间，一个进程就能同时代理 BTC、LTC、KAS、ZEC、ETC、BCH、CKB、SC、XBT、PRL 等币种的 Stratum 连接，并提供实时算力、份额、延迟与服务器状态面板。适合需要多矿池线路冗余、按端口配置费用策略、或想把多地矿场统一接入管理的场景。

对于不同地区的矿场，可配合 [CakeBox 客户端](https://github.com/hashultra/cakebox) 建立加密隧道，将矿机安全接入 HashCake，降低跨地域接入与线路维护的复杂度。

## 适用场景

- **矿场自建矿池代理 / 矿池中转**：多台矿机走统一入口，按矿池线路分流，主池异常时自动切到备池。
- **按端口配置费用策略（矿池抽水）**：可为每个端口设置费用矿池、钱包与分配比例，并持续对比目标比例与实际比例。
- **多币种统一管理**：不同算法、不同币种的代理端口共用一个后台，不必为每个币种单独维护一套代理。
- **异地矿场接入**：远端矿场用 CakeBox 建加密隧道回中心服务器，公网只暴露隧道入口。
- **算力运营监控**：实时查看在线与掉线设备、接受与拒绝份额、矿池延迟和服务器资源。

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

## 支持的币种与端口

HashCake 按端口配置币种，同一后台可以同时跑多种算法。已内置原生协议适配的币种：

| 币种 | 算法 / 协议 | 说明 |
| --- | --- | --- |
| BTC / BCH / BSV | SHA256d Stratum | 最常用的比特币系代理，支持主备矿池与 vardiff。 |
| LTC / DOGE | Scrypt Stratum | 按 scrypt 难度换算算力，可用 f2pool 等 scrypt 矿池。 |
| DASH | X11 Stratum | 独立难度换算，避免算力显示失真。 |
| ETC | Ethash / Etchash | 走 eth_submitLogin / getWork 方言。 |
| KAS | Kaspa HeavyHash | 支持两参数 notify 与带 nonce 的提交。 |
| ZEC | Equihash Stratum | 使用 mining.set_target 下发目标。 |
| CKB / SC / ALEO | Eaglesong / Sia / Aleo Stratum | 按币种独立适配的提交方言。 |
| XBT | Bitcoin BLAKE2b（DATUM 网关） | 经 DATUM 网关接入，走 Sia 方言 Stratum。 |
| PRL | Pearl Stratum | 76 字节头 + 256 位目标的对象参数方言。 |

其它币种或暂未适配的方言可以用 `currency: RELAY` 做纯中转：只转发矿机与矿池之间的原始 Stratum 字节流，不做任务改写、不抽水、不计算力。

已知限制（按此判断该用原生币种还是 RELAY）：

- **ALEO**：目前只对**同一证明地址**的费用通道生效；跨证明地址切换、非空服务端 nonce 与未知方言仍请用 RELAY。
- **ETC+ZIL 双挖**：按 RELAY 处理，不当作 ETC 启动。
- **XBT**：必须经 DATUM 网关接入，矿池需提供 DATUM 入口。
- 其余币种的未知矿池方言同样走 RELAY，不静默按相似币种启动。

## 常见问题

**HashCake 支持哪些币种？**
原生支持 BTC、BCH、BSV、LTC、DOGE、DASH、ETC、KAS、ZEC、CKB、SC、ALEO、XBT、PRL；其它方言可用 RELAY 纯中转，只转发字节流。

**HashCake 和 CakeBox 是什么关系？**
HashCake 是中心服务端代理，CakeBox 是部署在矿场的客户端，两者通过加密隧道连接。只在本机接入矿机时，单独部署 HashCake 即可；矿场与服务器跨地域时再加 CakeBox。

**可以在国内服务器上安装吗？**
可以。README 的「国内服务器」入口使用国内镜像获取安装脚本和二进制，安装器仍会用 SHA256SUMS 校验每个下载文件。

**升级会不会丢配置和账号？**
不会。更新保留 Web 端口、安全访问路径、账号、令牌、配置与状态目录；新版本启动失败时安装器自动回滚到旧二进制、旧服务文件和原有防火墙状态。

**Windows 能用吗？**
可以用。Windows amd64 程序与 Linux 使用同一正式版本，从 Releases 页面下载对应版本的 `.exe`；Windows 服务与后台功能与 Linux 一致。

