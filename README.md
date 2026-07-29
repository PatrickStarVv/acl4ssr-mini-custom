# Custom ACL4SSR Config (Mini 精简自用版)

本项目是基于 ACL4SSR 规则集深度定制的 Clash / Mihomo 转换配置文件（`.ini`）。旨在提供一个**极简、高效、注重隐私安全**的分流方案，特别适合对 **AI 平台（ChatGPT/Claude）风控敏感** 以及追求 **界面干净度** 的用户。

---

## 🌟 配置特点与设计理念

1. **Mini 精简分流（轻量化）**
   * 精简臃肿的规则集，仅保留常用核心分流（Telegram、微软、GoogleCN、SteamCN、ProxyMedia 等）。
   * 降低 Clash 内核 CPU 与内存占用，后台运行无感流畅。

2. **UI 纯净与排序优化**
   * 配合订阅转换参数，彻底移除 `节点选择` 组中的 `DIRECT` 选项，杜绝误选导致直连泄漏。
   * 节点剔除国旗 Emoji，并通过正则自动化分类重命名（格式如：`A-台湾01`、`D-美国03`），界面一目了然。

3. **高安全与高可用策略**
   * **禁用 TLS 跳过验证 (`scv=false`)**：强制进行 TLS 证书校验，确保 AI 使用过程中的数据传输安全与 IP 纯净，防止风控封号。
   * **开启 UDP 转发 (`udp=true`)**：保障 Telegram 语音通话及 YouTube 等流媒体的最佳加载性能。
   * **故障转移保障**：引入 `fallback` 自动选择可用节点，确保网络持续在线。

---

## 🚀 订阅转换参数模版

为保护个人隐私，下述模版中的机场订阅链接已使用占位符替代。将 `YOUR_AIRPORT_URL_1|YOUR_AIRPORT_URL_2` 替换为你自己的真实机场链接（多订阅用 `|` 分隔）即可：

### 订阅转换长链接 (模版)
```text
[https://api.wcc.best/sub?target=clash&url=YOUR_AIRPORT_URL_1%7CYOUR_AIRPORT_URL_2&insert=false&config=https%3A%2F%2Fraw.githubusercontent.com%2FPatrickStarVv%2Facl4ssr-mini-custom%2Frefs%2Fheads%2Fmain%2FACL4SSR_Mini_Custom.ini&include=TW.*(%3F%3A01%7C03%7C04)%7CUS.*(%3F%3A03%7C10)%7C%E6%96%B0%E5%8A%A0%E5%9D%A1.*(%3F%3ADRT%7CBGP)&emoji=false&list=false&tfo=false&scv=false&fdn=false&expand=false&sort=true&udp=true&new_name=true&rename=%5E.*(%3F%3ATW%7C%E5%8F%B0%E6%B9%BE).*01.*%24%40A-%E5%8F%B0%E6%B9%BE01%60%5E.*(%3F%3ATW%7C%E5%8F%B0%E6%B9%BE).*04.*%24%40B-%E5%8F%B0%E6%B9%BE04%60%5E.*(%3F%3ATW%7C%E5%8F%B0%E6%B9%BE).*03.*%24%40C-%E5%8F%B0%E6%B9%BE03%60%5E.*(%3F%3AUS%7C%E7%BE%8E%E5%9B%BD).*03.*%24%40D-%E7%BE%8E%E5%9B%BD03%60%5E.*(%3F%3AUS%7C%E7%BE%8E%E5%9B%BD).*10.*%24%40E-%E7%BE%8E%E5%9B%BD10%60%5E.*%E6%96%B0%E5%8A%A0%E5%9D%A1.*BGP.*%24%40F-%E6%96%B0%E5%8A%A0%E5%9D%A1BGP%60%5E.*%E6%96%B0%E5%8A%A0%E5%9D%A1.*DRT.*%24%40G-%E6%96%B0%E5%8A%A0%E5%9D%A1DRT](https://api.wcc.best/sub?target=clash&url=YOUR_AIRPORT_URL_1%7CYOUR_AIRPORT_URL_2&insert=false&config=https%3A%2F%2Fraw.githubusercontent.com%2FPatrickStarVv%2Facl4ssr-mini-custom%2Frefs%2Fheads%2Fmain%2FACL4SSR_Mini_Custom.ini&include=TW.*(%3F%3A01%7C03%7C04)%7CUS.*(%3F%3A03%7C10)%7C%E6%96%B0%E5%8A%A0%E5%9D%A1.*(%3F%3ADRT%7CBGP)&emoji=false&list=false&tfo=false&scv=false&fdn=false&expand=false&sort=true&udp=true&new_name=true&rename=%5E.*(%3F%3ATW%7C%E5%8F%B0%E6%B9%BE).*01.*%24%40A-%E5%8F%B0%E6%B9%BE01%60%5E.*(%3F%3ATW%7C%E5%8F%B0%E6%B9%BE).*04.*%24%40B-%E5%8F%B0%E6%B9%BE04%60%5E.*(%3F%3ATW%7C%E5%8F%B0%E6%B9%BE).*03.*%24%40C-%E5%8F%B0%E6%B9%BE03%60%5E.*(%3F%3AUS%7C%E7%BE%8E%E5%9B%BD).*03.*%24%40D-%E7%BE%8E%E5%9B%BD03%60%5E.*(%3F%3AUS%7C%E7%BE%8E%E5%9B%BD).*10.*%24%40E-%E7%BE%8E%E5%9B%BD10%60%5E.*%E6%96%B0%E5%8A%A0%E5%9D%A1.*BGP.*%24%40F-%E6%96%B0%E5%8A%A0%E5%9D%A1BGP%60%5E.*%E6%96%B0%E5%8A%A0%E5%9D%A1.*DRT.*%24%40G-%E6%96%B0%E5%8A%A0%E5%9D%A1DRT)
