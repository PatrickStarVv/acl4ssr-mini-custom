# 🛠️ 我的专属 Clash 订阅转换配置备忘录

这个仓库是用来存放我个人定制的 Clash 订阅转换规则文件的。主文件是 `ACL4SSR_Mini_Custom.ini`。

## 📌 这个 `.ini` 文件是干嘛用的？

简单来说，它是一张给“订阅转换服务器 (Subconverter)”看的**图纸**。

转换服务器会把我的“原始机场订阅”和这张“图纸”结合起来，生成一个专门给 Clash Verge 用的最终配置文件。我通过修改这个 `.ini` 文件，实现了以下目的：
1. **清理 UI 杂乱**：删除了机场冗余的策略组，只保留最核心的节点面板，界面清爽。
2. **极致轻量化**：引入外部规则集（Rule-Providers），大幅精简配置文件，Clash 启动秒开，极低内存占用。
3. **精准分流 (AI 与 TG 优化)**：
   * **AI 防封号**：开启证书验证并筛选优质节点，为 ChatGPT/Claude 提供最干净的专属防风控路线。
   * **TG 优化**：开启 UDP 支持，保障 Telegram 语音/视频通话低延迟、不断流。
   * **国内直连**：精准识别国内网络流量，不经过节点直连，省流量且秒开。

## 🚀 使用方法 (如何生成我的终极订阅链接)

我使用 `api.wcc.best` 作为转换后端。完整的订阅链接是由 **基础模板 + 我的私密机场链接** 拼成的。

### 1. 终极链接模板（切勿泄露真实机场链接！）
将下方链接中的 `【我的机场订阅链接(需URL Encode)】` 替换为真实的订阅地址即可使用。

```text
[https://api.wcc.best/sub?target=clash&url=](https://api.wcc.best/sub?target=clash&url=)【我的机场订阅链接(需URL Encode)】&insert=false&config=https%3A%2F%2Fraw.githubusercontent.com%2FPatrickStarVv%2Facl4ssr-mini-custom%2Frefs%2Fheads%2Fmain%2FACL4SSR_Mini_Custom.ini&include=TW.*(%3F%3A01%7C03%7C04)%7CUS.*(%3F%3A03%7C10)%7C%E6%96%B0%E5%8A%A0%E5%9D%A1.*(%3F%3ADRT%7CBGP)&emoji=false&list=false&tfo=false&scv=false&fdn=false&expand=false&sort=true&udp=true&new_name=true&rename=%5E.*(%3F%3ATW%7C%E5%8F%B0%E6%B9%BE).*01.*%24%40A-%E5%8F%B0%E6%B9%BE01%60%5E.*(%3F%3ATW%7C%E5%8F%B0%E6%B9%BE).*04.*%24%40B-%E5%8F%B0%E6%B9%BE04%60%5E.*(%3F%3ATW%7C%E5%8F%B0%E6%B9%BE).*03.*%24%40C-%E5%8F%B0%E6%B9%BE03%60%5E.*(%3F%3AUS%7C%E7%BE%8E%E5%9B%BD).*03.*%24%40D-%E7%BE%8E%E5%9B%BD03%60%5E.*(%3F%3AUS%7C%E7%BE%8E%E5%9B%BD).*10.*%24%40E-%E7%BE%8E%E5%9B%BD10%60%5E.*%E6%96%B0%E5%8A%A0%E5%9D%A1.*BGP.*%24%40F-%E6%96%B0%E5%8A%A0%E5%9D%A1BGP%60%5E.*%E6%96%B0%E5%8A%A0%E5%9D%A1.*DRT.*%24%40G-%E6%96%B0%E5%8A%A0%E5%9D%A1DRT
