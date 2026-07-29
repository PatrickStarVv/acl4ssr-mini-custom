# 🛠️ 我的专属 Clash 订阅转换配置备忘录

这个仓库是用来存放我个人定制的 Clash 订阅转换规则文件的。主文件是 `ACL4SSR_Mini_Custom.ini`。

## 📌 这个 `.ini` 文件是干嘛用的？

简单来说，它是一张给“订阅转换服务器 (Subconverter)”看的**图纸**。

转换服务器会把我的“原始机场订阅”和这张“图纸”结合起来，生成一个专门给 Clash Verge 用的最终配置文件。我通过修改这个 `.ini` 文件，实现了以下目的：
1. **清理 UI 杂乱 (定制专属策略组)**：
   原生的机场订阅往往会硬塞一大堆我根本用不到的策略组（比如各种眼花缭乱的地区分组、广告拦截开关、多余的 `DIRECT` 或 `REJECT` 等），导致客户端的“代理”界面极其臃肿。通过修改这个 `.ini` 文件，我把这些不需要手动干预的冗余选项全部隐藏或移除了，只保留了我最核心需要的精简面板。现在在 Clash Verge 里，我一眼就能看到我需要的节点，不用再费力往下拉，强迫症狂喜。

2. **极致轻量化 (引入 Rule-Providers)**：
   传统的配置文件会把几万条分流规则（记录了哪些网址走代理，哪些走直连）全部以纯文本形式塞进一个文件里，导致配置动辄几 MB 大小。这不仅让每次更新订阅变慢，还会严重拖慢 Clash 的启动速度，并占用大量电脑内存。
   我在这里使用了 **Rule-Providers（规则集）** 技术，相当于把庞大的规则库“外部链接”进来，交给后台悄悄拉取。再配合订阅链接里的 `expand=false` 参数，让最终下发给客户端的配置文件极其精简（可能只有几十行代码）。这让软件运行如丝般顺滑，毫无负担。

3. **精准的定制分流 (为 AI 与社交通讯保驾护航)**：
   我根据自己的高频使用场景，重新定义了底层路由逻辑，让流量各行其道：
   * **AI 专属通道**：像 ChatGPT、Claude 这种风控极严的平台，必须给它们划定最干净、最稳定的专用节点路线（比如排除掉容易被标记的 IP 段），最大程度防止频繁掉线、弹人机验证甚至封号。
   * **Telegram 优化**：针对 TG 的语音、视频及大文件传输需求，配合开启的 UDP 协议，确保走低延迟路线。
   * **国内日常直连**：精准识别国内常用软件和网页流量，让它们不经过节点直接走本地网络。既节省了机场的宝贵流量，又保证了国内网页的秒开体验。
---

## 🚀 使用方法 (如何生成我的终极订阅链接)

我使用 `api.wcc.best` 作为转换后端。完整的订阅链接是由 **基础模板 + 我的私密机场链接** 拼成的。

### 1. 终极链接模板（切勿泄露真实机场链接！）
将下方链接中的 `【我的机场订阅链接(需URL Encode)】` 替换为真实的订阅地址即可使用。

```text
[https://api.wcc.best/sub?target=clash&url=](https://api.wcc.best/sub?target=clash&url=)【我的机场订阅链接(需URL Encode)】&insert=false&config=https%3A%2F%2Fraw.githubusercontent.com%2FPatrickStarVv%2Facl4ssr-mini-custom%2Frefs%2Fheads%2Fmain%2FACL4SSR_Mini_Custom.ini&include=TW.*(%3F%3A01%7C03%7C04)%7CUS.*(%3F%3A03%7C10)%7C%E6%96%B0%E5%8A%A0%E5%9D%A1.*(%3F%3ADRT%7CBGP)&emoji=false&list=false&tfo=false&scv=false&fdn=false&expand=false&sort=true&udp=true&new_name=true&rename=%5E.*(%3F%3ATW%7C%E5%8F%B0%E6%B9%BE).*01.*%24%40A-%E5%8F%B0%E6%B9%BE01%60%5E.*(%3F%3ATW%7C%E5%8F%B0%E6%B9%BE).*04.*%24%40B-%E5%8F%B0%E6%B9%BE04%60%5E.*(%3F%3ATW%7C%E5%8F%B0%E6%B9%BE).*03.*%24%40C-%E5%8F%B0%E6%B9%BE03%60%5E.*(%3F%3AUS%7C%E7%BE%8E%E5%9B%BD).*03.*%24%40D-%E7%BE%8E%E5%9B%BD03%60%5E.*(%3F%3AUS%7C%E7%BE%8E%E5%9B%BD).*10.*%24%40E-%E7%BE%8E%E5%9B%BD10%60%5E.*%E6%96%B0%E5%8A%A0%E5%9D%A1.*BGP.*%24%40F-%E6%96%B0%E5%8A%A0%E5%9D%A1BGP%60%5E.*%E6%96%B0%E5%8A%A0%E5%9D%A1.*DRT.*%24%40G-%E6%96%B0%E5%8A%A0%E5%9D%A1DRT
