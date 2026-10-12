# ACL4SSR Mini 自用规则

用于 Clash / Mihomo 的订阅转换配置，保留常用直连、广告拦截、通用代理和 Gemini 分流。

## 分流规则

| 流量 | 策略组 |
|---|---|
| 局域网、白名单、GoogleCN、SteamCN、微软规则集、国内流量 | 🌐 本地直连 |
| Gemini 规则集、Google AI Studio | ✨ Gemini |
| Telegram、通用外网服务，包括 ChatGPT | 🚀 节点选择 |
| 广告及应用内广告 | 🛡️ 广告拦截 |
| 未匹配流量 | 🐟 漏网之鱼 |

规则按配置顺序匹配。`ProxyMedia` 和 `ProxyLite` 覆盖范围不同，均保留。

`⚡ 自动选择` 使用 `fallback`，当前节点不可用时按候选顺序回退，不按最低延迟选节点。测速成功仅代表测试地址可达。

## 使用方法

1. 在订阅转换服务中使用 `ACL4SSR_Mini_Custom.ini`，输出格式选择 Clash。节点筛选、重命名和排序由转换参数控制。
2. 将转换后的订阅链接导入 Clash Verge，使用规则模式，通过系统代理或 TUN 接管流量。
3. 在 Gemini 组中选择可用节点，AI Studio 页面与 Gemini API 使用同一策略组。
4. 更新 GitHub 配置后，更新 Clash Verge 当前订阅，确认 `aistudio.google.com` 指向 Gemini 组。

## 订阅转换模板

将各原始订阅链接分别进行 URL 编码，再替换两个 `YOUR_AIRPORT_URL_*` 占位符。单订阅时删除 `%7CYOUR_AIRPORT_URL_2`。

```text
https://api.wcc.best/sub?target=clash&url=YOUR_AIRPORT_URL_1%7CYOUR_AIRPORT_URL_2&insert=false&config=https%3A%2F%2Fraw.githubusercontent.com%2FPatrickStarVv%2Facl4ssr-mini-custom%2Frefs%2Fheads%2Fmain%2FACL4SSR_Mini_Custom.ini&include=TW.*(%3F%3A01%7C03%7C04)%7CUS.*(%3F%3A03%7C10)%7C%E6%96%B0%E5%8A%A0%E5%9D%A1.*(%3F%3ADRT%7CBGP)&emoji=false&list=false&tfo=false&scv=false&fdn=false&expand=false&sort=true&udp=true&new_name=true&rename=%5E.*(%3F%3ATW%7C%E5%8F%B0%E6%B9%BE).*01.*%24%40A-%E5%8F%B0%E6%B9%BE01%60%5E.*(%3F%3ATW%7C%E5%8F%B0%E6%B9%BE).*04.*%24%40B-%E5%8F%B0%E6%B9%BE04%60%5E.*(%3F%3ATW%7C%E5%8F%B0%E6%B9%BE).*03.*%24%40C-%E5%8F%B0%E6%B9%BE03%60%5E.*(%3F%3AUS%7C%E7%BE%8E%E5%9B%BD).*03.*%24%40D-%E7%BE%8E%E5%9B%BD03%60%5E.*(%3F%3AUS%7C%E7%BE%8E%E5%9B%BD).*10.*%24%40E-%E7%BE%8E%E5%9B%BD10%60%5E.*%E6%96%B0%E5%8A%A0%E5%9D%A1.*BGP.*%24%40F-%E6%96%B0%E5%8A%A0%E5%9D%A1BGP%60%5E.*%E6%96%B0%E5%8A%A0%E5%9D%A1.*DRT.*%24%40G-%E6%96%B0%E5%8A%A0%E5%9D%A1DRT
```

`scv=false` 保留 TLS 节点的证书检查；`udp=true` 请求开启 UDP，实际可用性取决于节点协议和服务端支持。
