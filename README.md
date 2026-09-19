# IEPL 国际专线：按业务场景选对线路和套餐，Mkcloud 全线价格与优惠码盘点

搜“IEPL 国际专线”的人，大多是遇到同一类麻烦：业务连海外平台时断时续、IP 被平台风控盯上、晚高峰上传卡成幻灯片，普通 VPS 换了好几家都解决不了。这篇文章把 IEPL 专线讲清楚——它是什么、和普通 VPS 的区别在哪、什么业务值得买、买之前要过哪些门槛，并以 Mkcloud 这家专线服务商为例，把当前在售的全部线路和价格列成表，方便你直接对号入座。

所有价格和套餐信息来自 2026 年 9 月 Mkcloud 官网商店页面的实时抓取，优惠码部分会单独标注活动状态。

## IEPL 专线到底是什么，先说清楚再谈买

IEPL（International Ethernet Private Line，国际以太网专线）本质上是运营商提供的一条点对点二层电路：两端设备在链路层直连，数据不走公共互联网，不经过公网拥塞和审查节点。这也是它和普通 VPS 最根本的区别——普通 VPS 的流量和你自己的宽带一样走公网，丢包、限速、绕路都不可控；专线则用一条私有通道把国内入口和海外出口连起来，稳定性由线路资源保证，而不是靠碰运气。

不过要注意一点：IEPL 描述的只是“一条好线路”，线路本身不等于合规服务。目前市面上以“IEPL 专线机场”名义向公众售卖跨境代理订阅的做法属于违规经营，Mkcloud 这类服务商的产品形态也不是机场订阅，而是一台可以 SSH/远程桌面登录的专线 VPS：你在服务器里运行业务程序，流量自动从专线出口访问目标。官方条款明确禁止机场、回国等用途，购买需要中国身份实名，直连产品还绑定省份白名单，一个账号只允许一个省份的 IP 连入。

另外一个容易被忽略的技术细节：Mkcloud 所有套餐都是“单端双独立 IP”——每台机器配 1 个独立入口 IP 和 1 个独立出口 IP，但出口端不接受外部连入。也就是说，它适合“从 VPS 内主动访问海外业务”的场景，不能拿来建公开网站、跑游戏服务端或接收支付回调。

## Mkcloud 是谁：只做一件事的专线服务商

Mkcloud 是 2023 年成立的国内专线云服务商，产品线很集中：IEPL、IPLC 专线 VPS 和 IX 云内网接入，覆盖广东、上海、福建三处国内入口，香港、日本、美国三个海外出口，外加一个上海 CN2 国内优化产品。付款支持支付宝，全线月付起订。

它的线路卖点在出口侧：香港 BGP 出口接入 PCCW、NTT、Cogent、Lumen、Telstra 等多家上游，进 Equinix IX 和 HKIX 交换中心，并对 Google、Cloudflare、Valve 等搭了私有 PNI 对等连接。第三方测评站 vps.dance 对早期广港套餐做过完整测试：出口 IP 的 Scamalytics 欺诈评分为 0/100，单线程下载跑出 130Mbps 上下，广州入口 TCP ping 电信 34ms、联通 33ms、移动 38ms。测试距今已有一段时间，套餐 lineup 也换了几轮，但能看出线路底子。

延迟数字要按官方口径理解：官网上标注的 1~2ms、25~28ms 这些都是“端内延迟”，即专线通道内部的耗时，不是你本地到目标网站的全程延迟。全程延迟还取决于你家宽到入口、出口到目标两段公网。

## 买之前先过一遍：你的业务需不需要 IEPL 国际专线

Mkcloud 官方知识库里有一张“60 秒选线表”，逻辑很实用，照着问自己五个问题：

1. **业务能不能在 VPS 里跑？** 店铺后台、ERP、API 调用、直播推流工具可以；必须接收公网主动连接的业务（建站、邮件接收、回调）不行。
2. **目标市场在哪？** 出口决定线路——东南亚和港区业务选香港出口，日本市场选日本，美国区选美国。
3. **你从什么网络接入？** 家宽/本地宽带选直连产品（绑定省份），已经有云服务器选 IX 产品（云厂内网接入，不限省份但要付前置机钱）。
4. **流量怎么用？** 用量集中、可估算选流量计费；长时间持续跑选独享带宽（不限流量）。
5. **要不要高防？** 有明确防护需求走福建高防线路，防护阈值需要开工单确认。

两条容易踩的坑值得提前说：

> 流量计费套餐的流量按上行和下行双向合并统计，实际可用量比想象中少一半；IXP 产品超量后直接停机，需要买流量重置或升级套餐。

> IXP（上云互联优化）产品只能从指定云厂 BGP 网络连入，深港线路支持腾讯云、百度云国内全网和火山云、华为云华南（阿里云国内全网暂不通），沪方向则要求华东节点。你需要先有一台符合条件的云前置机，这笔钱要算进总成本。

另外，“共享”和“独享”指的是带宽，不是 IP——两类套餐每台机器都是双独立 IP，这点对防关联业务反而友好。

## Mkcloud 全线套餐与价格（2026 年 9 月官网实时价）

以下是官网当前展示的全部在售套餐。参考延迟均为端内值；流量计费套餐按双向合计统计，独享带宽套餐不限流量。

### 香港方向：广港 IEPL · 广州 BGP 入口（流量计费，端内延迟 1~2ms）

| 套餐（CPU/内存/硬盘） | 峰值带宽 | 月流量 | 月付 | 购买链接 |
| --- | --- | --- | --- | --- |
| 1核/2GB/20GB | 200M | 1TB | ¥358 | [ 查看广港 IEPL 实时价格](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fgz-hk-sh) |
| 2核/4GB/40GB | 300M | 2TB | ¥568 | [ 查看实时价格](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fgz-hk-sh) |
| 2核/4GB/40GB | 300M | 4TB | ¥998 | [ 查看实时价格](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fgz-hk-sh) |
| 4核/8GB/60GB | 500M | 6TB | ¥1388 | [ 查看实时价格](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fgz-hk-sh) |
| 4核/8GB/60GB | 500M | 10TB | ¥2288 | [ 查看实时价格](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fgz-hk-sh) |
| 4核/8GB/60GB | 1G | 20TB | ¥4500 | [ 查看实时价格](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fgz-hk-sh) |

入口为腾讯广州八线 BGP，出口香港 BGP，每台配独享 IPv4 ×2（进+出）。

### 广港 IEPL · 独享带宽（广州 BGP 入口，流量不限，端内 1~2ms）

| 带宽档 | 配置 | 月付 | 购买链接 |
| --- | --- | --- | --- |
| 5M 独享 | 2核/4GB/40GB | ¥500 | [ 选广港独享带宽套餐](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fgz-hk-ex) |
| 10M 独享 | 2核/4GB/40GB | ¥700 | [ 查看档位](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fgz-hk-ex) |
| 20M 独享 | 2核/4GB/40GB | ¥1320 | [ 查看档位](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fgz-hk-ex) |
| 50M 独享 | 4核/8GB/60GB | ¥3150 | [ 查看档位](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fgz-hk-ex) |
| 100M 独享 | 4核/8GB/60GB | ¥5800 | [ 查看档位](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fgz-hk-ex) |
| 200M 独享 | 4核/8GB/60GB | ¥11600 | [ 查看档位](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fgz-hk-ex) |
| 300M 独享 | 4核/8GB/60GB | ¥17400 | [ 查看档位](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fgz-hk-ex) |

更高带宽支持定制，按需议价。

### 广港 IEPL · 广东移动入口大带宽独享（端内 1~2ms）

| 带宽档 | 配置 | 月付 | 购买链接 |
| --- | --- | --- | --- |
| 1G 独享 | 28核/64GB/512GB，赠独立服务器 | ¥17000 | [ 咨询广东移动大带宽专线](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fgz-yd-hk-ex) |
| 2G 独享 | 28核/64GB/512GB | ¥32000 | [ 查看配置](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fgz-yd-hk-ex) |
| 5G 独享 | 28核/64GB/512GB | ¥75000 | [ 查看配置](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fgz-yd-hk-ex) |

这款含 300Gbps DDoS 高防，且无跨省 QoS 限制、无省份限制，是给直播团队和大流量场景准备的。

### 深港 IX · 上云互联优化入口（云厂接入，超量停机，端内 1~2ms）

| 配置 | 峰值带宽 | 月流量 | 月付 | 购买链接 |
| --- | --- | --- | --- | --- |
| 2核/4GB/40GB | 1G | 2TB | ¥158 | [ 选购深港 IX 专线](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fcloud-hk-sh) |
| 2核/4GB/40GB | 1G | 4TB | ¥258 | [ 查看档位](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fcloud-hk-sh) |
| 4核/8GB/40GB | 2G | 6TB | ¥378 | [ 查看档位](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fcloud-hk-sh) |
| 4核/8GB/40GB | 2G | 10TB | ¥826 | [ 查看档位](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fcloud-hk-sh) |
| 4核/8GB/40GB | 2G | 20TB | ¥1639 | [ 查看档位](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fcloud-hk-sh) |
| 4核/8GB/60GB | 3G | 30TB | ¥2458 | [ 查看档位](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fcloud-hk-sh) |
| 8核/8GB/60GB | 3G | 50TB | ¥3588 | [ 查看档位](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fcloud-hk-sh) |
| 8核/16GB/80GB | 5G | 100TB | ¥7168 | [ 查看档位](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fcloud-hk-sh) |
| 8核/16GB/80GB | 5G | 200TB | ¥12288 | [ 查看档位](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fcloud-hk-sh) |
| 8核/16GB/80GB | 5G | 300TB | ¥18428 | [ 查看档位](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fcloud-hk-sh) |

这是全线入门价最低的一条路：2TB 流量月付 158 元。代价是必须有云厂前置机，且超量即停机。

### 福建高防 · 厦门 BGP 入口独享（默认含 100Gbps DDoS，端内 1~2ms）

| 带宽档 | 配置 | 月付 | 购买链接 |
| --- | --- | --- | --- |
| 200M 独享 | 4核/8GB/40GB | ¥6000 | [ 查看厦港高防专线](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fxm-hk-ex) |
| 500M 独享 | 8核/8GB/60GB | ¥13500 | [ 查看配置](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fxm-hk-ex) |
| 1G 独享 | 28核/64GB/512GB | ¥24000 | [ 查看配置](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fxm-hk-ex) |
| 2G 独享 | 28核/64GB/512GB | ¥46000 | [ 查看配置](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fxm-hk-ex) |
| 5G 独享 | 28核/64GB/512GB | ¥110000 | [ 查看配置](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fxm-hk-ex) |

泉州电信入口的泉港线路是同类高防产品，200M 独享 4200 元/月起，具体防护阈值两家都需要开工单确认（[👉 咨询泉港高防专线](https://bit.ly/MKCLoud)）。

### 日本方向：沪日 IPLC · 上海电信入口（流量计费，端内 25~28ms）

| 套餐（CPU/内存/硬盘） | 峰值带宽 | 月流量 | 月付 | 购买链接 |
| --- | --- | --- | --- | --- |
| 1核/2GB/20GB | 200M | 1TB | ¥358 | [ 查看沪日 IPLC 套餐](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fsh-jp-sh) |
| 2核/4GB/40GB | 300M | 2TB | ¥568 | [ 查看套餐](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fsh-jp-sh) |
| 2核/4GB/40GB | 300M | 4TB | ¥998 | [ 查看套餐](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fsh-jp-sh) |
| 4核/8GB/60GB | 500M | 6TB | ¥1388 | [ 查看套餐](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fsh-jp-sh) |
| 4核/8GB/60GB | 500M | 10TB | ¥2288 | [ 查看套餐](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fsh-jp-sh) |
| 4核/8GB/60GB | 1G | 20TB | ¥4500 | [ 查看套餐](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fsh-jp-sh) |

### 沪日 IPLC · 独享带宽（上海电信入口，流量不限）

| 带宽档 | 配置 | 月付 | 购买链接 |
| --- | --- | --- | --- |
| 5M 独享 | 2核/4GB/40GB | ¥600 | [ 选沪日独享带宽](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fsh-jp-ex) |
| 10M 独享 | 2核/4GB/40GB | ¥800 | [ 查看档位](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fsh-jp-ex) |
| 20M 独享 | 2核/4GB/40GB | ¥1560 | [ 查看档位](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fsh-jp-ex) |
| 50M 独享 | 4核/8GB/60GB | ¥3500 | [ 查看档位](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fsh-jp-ex) |
| 100M 独享 | 4核/8GB/60GB | ¥6000 | [ 查看档位](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fsh-jp-ex) |
| 200M 独享 | 4核/8GB/60GB | ¥12000 | [ 查看档位](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fsh-jp-ex) |
| 300M 独享 | 4核/8GB/60GB | ¥18000 | [ 查看档位](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fsh-jp-ex) |

### 沪日 IX · 云厂接入（超量停机，端内 25~28ms）

| 配置 | 峰值带宽 | 月流量 | 月付 | 购买链接 |
| --- | --- | --- | --- | --- |
| 2核/4GB/40GB | 200M | 1TB | ¥166 | [ 选购沪日 IX 专线](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fcloud-jp-sh) |
| 2核/4GB/40GB | 300M | 2TB | ¥268 | [ 查看档位](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fcloud-jp-sh) |
| 2核/4GB/40GB | 500M | 3TB | ¥358 | [ 查看档位](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fcloud-jp-sh) |
| 4核/8GB/40GB | 1G | 6TB | ¥688 | [ 查看档位](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fcloud-jp-sh) |
| 4核/8GB/40GB | 1G | 10TB | ¥1125 | [ 查看档位](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fcloud-jp-sh) |
| 4核/8GB/40GB | 1G | 20TB | ¥2150 | [ 查看档位](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fcloud-jp-sh) |
| 4核/8GB/60GB | 2G | 30TB | ¥3165 | [ 查看档位](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fcloud-jp-sh) |
| 8核/8GB/60GB | 2G | 50TB | ¥5222 | [ 查看档位](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fcloud-jp-sh) |

### 美国方向：沪美 IPLC · 上海电信入口（流量计费，端内 124~134ms）

| 套餐（CPU/内存/硬盘） | 峰值带宽 | 月流量 | 月付 | 购买链接 |
| --- | --- | --- | --- | --- |
| 1核/2GB/20GB | 200M | 1TB | ¥428 | [ 查看沪美 IPLC 套餐](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fsh-us-sh) |
| 2核/4GB/40GB | 300M | 2TB | ¥698 | [ 查看套餐](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fsh-us-sh) |
| 2核/4GB/40GB | 300M | 4TB | ¥1258 | [ 查看套餐](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fsh-us-sh) |
| 4核/8GB/60GB | 500M | 6TB | ¥1758 | [ 查看套餐](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fsh-us-sh) |
| 4核/8GB/60GB | 500M | 10TB | ¥2888 | [ 查看套餐](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fsh-us-sh) |
| 4核/8GB/60GB | 1G | 20TB | ¥5666 | [ 查看套餐](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fsh-us-sh) |

### 沪美 IPLC · 独享带宽（UCloud 上海 BGP 入口，流量不限）

| 带宽档 | 配置 | 月付 | 购买链接 |
| --- | --- | --- | --- |
| 5M 独享 | 2核/4GB/40GB | ¥850 | [ 选沪美独享带宽](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fshh-us-ex) |
| 10M 独享 | 2核/4GB/40GB | ¥1300 | [ 查看档位](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fshh-us-ex) |
| 20M 独享 | 2核/4GB/40GB | ¥2560 | [ 查看档位](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fshh-us-ex) |
| 50M 独享 | 4核/8GB/60GB | ¥6000 | [ 查看档位](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fshh-us-ex) |
| 100M 独享 | 4核/8GB/60GB | ¥11500 | [ 查看档位](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fshh-us-ex) |

### 沪美 IX · 云厂接入（超量停机，端内 124~134ms）

| 配置 | 峰值带宽 | 月流量 | 月付 | 购买链接 |
| --- | --- | --- | --- | --- |
| 2核/4GB/40GB | 200M | 1TB | ¥266 | [ 选购沪美 IX 专线](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fcloud-us-sh) |
| 2核/4GB/40GB | 200M | 2TB | ¥430 | [ 查看档位](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fcloud-us-sh) |
| 2核/4GB/40GB | 500M | 3TB | ¥615 | [ 查看档位](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fcloud-us-sh) |
| 4核/8GB/40GB | 500M | 6TB | ¥1166 | [ 查看档位](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fcloud-us-sh) |
| 4核/8GB/40GB | 1G | 10TB | ¥1945 | [ 查看档位](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fcloud-us-sh) |
| 4核/8GB/40GB | 1G | 20TB | ¥3686 | [ 查看档位](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fcloud-us-sh) |
| 4核/8GB/60GB | 2G | 30TB | ¥5529 | [ 查看档位](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fcloud-us-sh) |
| 8核/8GB/60GB | 2G | 50TB | ¥9216 | [ 查看档位](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fcloud-us-sh) |

### 沪港方向与上海 CN2

沪港方向走“上海-香港 IPLC”，云厂接入版端内 21ms：2核4G/500M/2TB 月付 ¥198，3TB ¥288，4核8G/1G/6TB ¥398，10TB ¥666，20TB ¥1290，30TB（2G 峰值）¥1900，50TB（2G 峰值）¥3120（[👉 查看沪港专线价格](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fcloud-sh-hk-sh)）。独享带宽版从 UCloud 上海 BGP 接入：5M ¥650、10M ¥950、20M ¥1760、50M ¥4000、100M ¥7500（[👉 查看独享档位](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fsh-hk-ex)）。

上海 CN2 是国内优化产品，不是海外出口：8核/16GB/60GB、500M 独享、不限流量，月付 ¥4500，下单后 7 天内交付，当前活动期额外赠送上海 9929 出口（[👉 开通上海 CN2](https://www.mkcloud.net/aff.php?aff=390&url=https%3A%2F%2Fwww.mkcloud.net%2Findex.php%2Fstore%2Fsh-cn2-ex)）。

## 优惠码和省钱姿势

Mkcloud 的优惠码跟着活动走，近一年多轮活动中反复出现的是这两个：

| 优惠码 | 适用产品 | 折扣 | 状态 |
| --- | --- | --- | --- |
| MK-8.8 | 流量计费套餐 | 8.8 折循环优惠 | 近期活动反复出现，以结算页为准 |
| MK-7.8 | 独享带宽产品 | 首月 7.8 折 | 近期活动反复出现，以结算页为准 |

MK-8.8 是循环折扣，续费同样生效，长期持有价值最高。算笔账：广港 1TB 套餐原价 358 元/月，套上 8.8 折约 315 元，一年省下五百多块。MK-7.8 只免首月，适合先试水独享带宽。

此外还有一批已经结束的活动码，了解一下有助于判断价格水位：MK-IEPL-WELCOME 和 MK-IPLC-WELCOME（ respective 线路 9 折）、CLOUD-2T-NEW（上云 2TB 套餐 126 元/月的活动价）、MK-NEW（新客专享机 236 元/月）都已过期；IXCLOUD（6.9 折）是沪日 IX 预售期专用，预售结束后适用范围不明，能否使用以下单页弹出的折扣为准。新春活动的 8.5 折循环、深港 IXP 年付 399 元等限时套餐也均已结束，官方知识库明确表示“文中优惠码仅在活动期内有效”。

下单前建议先进结算页试一次折扣，能弹出金额再付款（[👉 带上优惠码去结算页试价](https://bit.ly/MKCLoud)）。

## 下单前必须知道的几条规矩

Mkcloud 的购买门槛比普通 VPS 高，这些条款都在购物车页面白纸黑字写着：

- **实名认证**：所有产品需要中国身份信息实名，姓名、身份证、手机号一致。
- **省级白名单**：直连产品只允许一个绑定省份的 IP 连入，出差换城市可以自行切换省份，但同一时间只有一个省份能用。
- **退款政策**：仅质量问题退款，且需要提交具体的延迟、速度数据作为证据，客服审核判断，不是无条件试用；开通后不支持更换地域。
- **超量规则**：计量型套餐超量后停机，可自助购买流量重置或补差价升级；套餐升级走工单，降级时差价不退。
- **用途限制**：禁止机场、回国等用途，违规清退不退款。

开通速度上，常规专线产品官方标注约 1 分钟自动开通，上海 CN2 因涉及资源交付需要 7 天。

## 哪些业务值得上专线，哪些是在浪费钱

结合价格和线路特性，这几类业务是明确的适配对象：

- **TikTok 直播推流**：1~2ms 的端内延迟加 200M 起步的峰值带宽，推流卡顿大概率能改善。但官方知识库自己也提醒：直播卡顿要区分编码、设备、本地上传和网络路径，账号审核问题不是专线能解决的。
- **多账号防关联运营**：每台机器独立出口 IP，一个店配一台机器，账号之间物理隔离。注意这些是机房 IP 而非住宅 IP，对 IP 纯度要求极高的业务要先测试。
- **ERP、店铺后台和海外 SaaS 日常操作**：稳定不掉线，高峰期不走公网，这是专线相对普通 VPS 最直接的体验差异。
- **美国区业务**：沪美方向端内 124~134ms 是物理距离决定的，跑 API 和后台操作没问题，对延迟敏感的场景要有预期。

反过来，这些情况别买：需要建站或对外提供服务的，出口不支持入站；想拿专线当机场分享给全组的，白名单机制直接堵死；只是追剧看流媒体的，第三方测试显示其 IDC IP 的流媒体解锁表现一般，花几百块月费不划算。预算极其有限、业务又都在云上的，可以先算一下深港 IX 加前置机的总成本，有时反而比直连套餐便宜。

## 常见问题

**IEPL 和 IPLC 怎么选？** 对使用者的区别主要是技术形态：IEPL 是以太网专线，IPLC 是传统电路专线，Mkcloud 两类产品同样配置下价格接近，端内延迟分别是 1~2ms（港线 IEPL）和 25~28ms（沪日 IPLC）。选线先看你的业务从哪个城市接入、目标市场在哪，线路名称是次要的。

**IP 是原生住宅 IP 吗？** 不是。出口是海外机房 IP，vps.dance 测试中 Scamalytics 评分为 0，干净度不错，但机房属性和住宅属性是两回事。官方也明确“独享服务器 IP 不保证住宅属性、历史信誉或账号安全”。

**多人合用一台可以吗？** 技术上没有限制，但省份白名单意味着所有使用者的出口 IP 环境相同，等于放弃了多账号隔离的意义，还不如各买各的。

**商家靠谱吗？** 运营两年多，第三方测评站有完整测试记录，月付制加上随时可以停费，试错成本可控。大额独享订单建议先开工单确认需求再付款。

## 最后一点建议

IEPL 国际专线的价值在于确定性：确定的路径、确定的 IP、确定的高峰期表现，价格自然比普通 VPS 高一截。下单前把三件事核清楚就行——业务能不能在 VPS 里跑、你的网络能不能连上入口、结算页的折扣码还灵不灵。确认完这三点再付款，基本不会买错。

[👉 去商店核一遍现价再下单](https://bit.ly/MKCLoud)
