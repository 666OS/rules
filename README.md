# Rules

This is an automatically generated rule file repository containing rule sets for various proxy software.

## Update

- Rule files are automatically updated daily
- Update time: 2:00 AM Beijing Time

## Rule Sets

### Directory Structure

| 目录 | 行为 | 格式 | 内容 | 性能 | 内存 | 软件 |
|------|-----------------|------|------|----------|----------|----------|
| `surge/` | RULE-SET | text | 任意规则类型 | 良好 | 略低 | Surge |
| `singbox/` | binary | srs | 二进制类型 | 优秀 | 低 | Sing-box |
| `singbox/` | source | json | 任意规则类型 | 一般 | 一般 | Sing-box |
| `singbox/domain/` | domain | srs | 域名/域名通配符 | 优秀 | 低 | Sing-box |
| `singbox/ip/` | ipcidr | srs | IPv4/IPv6 集合 | 优秀 | 低 | Sing-box |
| `mihomo/` | classical | text | 任意规则类型 | 一般 | 一般 | Mihomo系 |
| `mihomo/domain/` | domain | mrs | 域名/域名通配符 | 优秀 | 低 | Mihomo系 |
| `mihomo/ip/` | ipcidr | mrs | IPv4/IPv6 集合 | 优秀 | 低 | Mihomo系 |
| `mihomo/domain/` | domain | text | 域名/域名通配符 | 良好 | 略低 | Mihomo系 |
| `mihomo/ip/` | ipcidr | text | IPv4/IPv6 集合 | 良好 | 略低 | Mihomo系 |

### Rule Sets

| 文件名 | 包含内容 | 用途 |
|--------|----------|------|
| `Advertising` | 广告追踪 | 拦截各类广告投放、统计追踪服务，包含国内外主流广告平台 |
| `Tracking` | 用户追踪 | 拦截用户行为分析、数据收集服务，保护隐私安全 |
| `Private` | 私有网络 | 内网设备管理、路由器配置、本地服务访问 |
| `Direct` | 直连域名列表 | 国内可直连的常用服务，避免不必要的代理 |
| `Download` | 下载服务 | 文件下载、软件更新、资源分发服务 |
| `XPTV` | VOD资源相关 | VOD资源服务、直播平台访问 |
| `SystemOTA` | 系统OTA | 苹果系统升级服务 | 
| `AppleCN` | 苹果中国服务 | 苹果国内CDN、iCloud中国区、App Store中国区 |
| `Speedtest` | 测速服务域名 | 网络速度测试、带宽检测服务 |
| `AI` | AI服务 | ChatGPT、Claude、Gemini等主流AI服务 |
| `Telegram` | Telegram | Telegram官方及第三方客户端、API服务 |
| `SocialMedia` | 社交媒体 | Twitter、Instagram、TikTok等社交平台 |
| `NewsMedia` | 新闻媒体 | 国际新闻网站、媒体机构服务 |
| `Games` | 游戏平台 | Steam、Epic、游戏服务器、对战平台 |
| `Crypto` | 货币相关服务 | 数字货币交易所、钱包、区块链服务 |
| `Emby` | Emby服务 | Emby媒体服务器、第三方Emby服务 |
| `Streaming` | 流媒体 | Netflix、Disney+、HBO等国际流媒体 |
| `Apple` | 苹果服务 | 苹果全球服务、iCloud、App Store国际区 |
| `Google` | 谷歌服务 | Google搜索、Gmail、YouTube、Google Drive |
| `Microsoft` | 微软服务 | Outlook、OneDrive、Teams、Azure服务 |
| `Facebook` | Facebook | Facebook、Instagram、WhatsApp、Meta服务 |
| `Proxy` | 代理服务列表 | 国外代理、VPN、科学上网服务 |
| `China` | 中国网站列表 | 国内网站、服务，确保直连访问 |

### Usage Example

#### 规则集示例

```yaml
BehaviorDN: &BehaviorDN {type: http, behavior: domain, format: mrs, interval: 86400}
BehaviorIP: &BehaviorIP {type: http, behavior: ipcidr, format: mrs, interval: 86400}

rule-providers: 
  # 域名规则
  Proxy: {<<: *BehaviorDN, url: https://github.com/666OS/rules/raw/release/mihomo/domain/Proxy.mrs}
  China: {<<: *BehaviorDN, url: https://github.com/666OS/rules/raw/release/mihomo/domain/China.mrs}
  
  # IP规则
  ProxyIP: {<<: *BehaviorIP, url: https://github.com/666OS/rules/raw/release/mihomo/ip/Proxy.mrs}
  ChinaIP: {<<: *BehaviorIP, url: https://github.com/666OS/rules/raw/release/mihomo/ip/China.mrs}
```

#### 规则配置示例

```yaml
rules:
  # 拦截规则
  - RULE-SET,Tracking,REJECT
  - RULE-SET,Advertising,REJECT
  - RULE-SET,SystemOTA,系统升级
  # 域名规则
  - RULE-SET,Private,直接连接
  - RULE-SET,Direct,直接连接
  - RULE-SET,XPTV,直接连接
  - RULE-SET,AppleCN,直接连接
  - RULE-SET,AI,人工智能
  - DOMAIN-KEYWORD,speedtest,网络测试
  - RULE-SET,Speedtest,网络测试
  - RULE-SET,Telegram,电报消息
  - RULE-SET,SocialMedia,社交平台
  - RULE-SET,Games,游戏平台
  - RULE-SET,Crypto,货币平台
  - RULE-SET,Emby,Emby服务
  - RULE-SET,Streaming,国际媒体
  - RULE-SET,NewsMedia,新闻媒体
  - RULE-SET,Apple,苹果服务 
  - RULE-SET,Google,谷歌服务
  - RULE-SET,Microsoft,微软服务
  - RULE-SET,Facebook,脸书服务
  - RULE-SET,Cloudflare,直接连接
  - RULE-SET,Proxy,国外流量
  - RULE-SET,China,国内流量

  # IP规则
  - RULE-SET,AdvertisingIP,REJECT
  - RULE-SET,PrivateIP,直接连接,no-resolve
  - RULE-SET,XPTVIP,直接连接,no-resolve
  - RULE-SET,AIIP,人工智能,no-resolve
  - RULE-SET,TelegramIP,电报消息,no-resolve
  - RULE-SET,SocialMediaIP,社交平台,no-resolve
  - RULE-SET,EmbyIP,Emby服务,no-resolve
  - RULE-SET,StreamingIP,国际媒体,no-resolve
  - RULE-SET,GoogleIP,谷歌服务,no-resolve
  - RULE-SET,FacebookIP,脸书服务,no-resolve
  - RULE-SET,CloudflareIP,直接连接,no-resolve
  - RULE-SET,ProxyIP,国外流量,no-resolve
  - RULE-SET,ChinaIP,国内流量,no-resolve

  # 兜底规则
  - MATCH,兜底流量
```

## Data Sources

- [@666OS/YYDS](https://github.com/666OS/YYDS)
- [@SagerNet/sing-box](https://github.com/SagerNet/sing-box)
- [@MetaCubeX/mihomo](https://github.com/MetaCubeX/mihomo)
- [@Loyalsoldier/domain-list-custom](https://github.com/Loyalsoldier/domain-list-custom)
- [@Loyalsoldier/geoip](https://github.com/Loyalsoldier/geoip)
- [@ConnersHua/RuleGo](https://github.com/ConnersHua/RuleGo)
- [@Blankwonder/surge-list](https://github.com/Blankwonder/surge-list)
- [@blackmatrix7/ios_rule_script](https://github.com/blackmatrix7/ios_rule_script)
- [@LM-Firefly/Rules](https://github.com/LM-Firefly/Rules)

## License

This project is licensed under the GNU General Public License v3.0.
8964

