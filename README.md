# MoonTV/LunaTV 配置编辑器（自用）
https://hafrey1.github.io/LunaTV-config  

--- 

##  MoonTV/LunaTV配置
订阅使用：复制下面链接  

👉 Base58编码订阅链接[精简版🎬源链接](https://raw.githubusercontent.com/hafrey1/LunaTV-config/refs/heads/main/jin18.txt)    （推荐使用自己部署的代理）精简版禁18源

```bash
https://pz.168188.dpdns.org?format=2&source=jin18
```
```bash
https://raw.githubusercontent.com/hafrey1/LunaTV-config/refs/heads/main/jin18.txt
```
👉 Base58编码订阅链接[精简版🎬+🔞源链接](https://raw.githubusercontent.com/hafrey1/LunaTV-config/refs/heads/main/jingjian.txt) （推荐使用自己部署的代理）精简版剔除无搜索结果和污染搜索结果源                             
```bash
https://pz.168188.dpdns.org?format=2&source=jingjian
```
```bash
https://raw.githubusercontent.com/hafrey1/LunaTV-config/refs/heads/main/jingjian.txt
```

👉 Base58编码订阅链接[完整版🎬+🔞源链接](https://raw.githubusercontent.com/hafrey1/LunaTV-config/refs/heads/main/LunaTV-config.txt) （推荐使用自己部署的代理）                          
```bash
https://pz.168188.dpdns.org?format=2&source=full
```
```bash
https://raw.githubusercontent.com/hafrey1/LunaTV-config/refs/heads/main/LunaTV-config.txt
```

--- 

# 🌐 CORSAPI（API 代理 & JSON 订阅器）

这是一个基于 **Cloudflare Workers** 的中转代理 + JSON 配置前缀替换工具。

支持将 API 请求通过 Worker 转发，并自动为 JSON 配置中的 `api` 字段添加/替换前缀。

同时支持生成 **Base58 编码的订阅格式**，并提供**多种配置源选择**，方便在外部应用中快速使用。

---

<details>
<summary>🚀 部署方法</summary>
  
#   
  
## 🚀 部署方法

1. 登录 [Cloudflare Dashboard](https://dash.cloudflare.com)
2. 新建一个 **Workers & Pages → Worker**
3. 将 `worker.js` 代码粘贴到编辑器中
4. 保存并部署
5. 绑定自定义域名（可选）

部署完成后，你就拥有了自己的 API 代理与订阅转换服务！

---   

</details>

<details>
<summary>🔗 使用示例</summary>
  
#  

假设你的 Worker 部署在：[`https://api.example.workers.dev`](https://api.example.workers.dev)

### 示例 1：代理任意 API

```
https://api.example.workers.dev/?url=https://ikunzyapi.com/api.php/provide/vod/
```

### 示例 2：获取原始 JSON 配置（精简+成人版）

```jsx
https://api.example.workers.dev/?format=0&source=jingjian
```

### 示例 3：获取代理前缀的 JSON 配置（精简+成人版）

```jsx
https://api.example.workers.dev/?format=1&source=jingjian
```

### 示例 4：获取原始 Base58 编码（精简+成人版）

```jsx
https://api.example.workers.dev/?format=2&source=jingjian
```

### 示例 5：获取代理前缀的 Base58 编码订阅（精简+成人版）

```jsx
https://api.example.workers.dev/?format=3&source=jingjian
```

### 示例 6：自定义代理前缀

```jsx
https://api.example.workers.dev/?format=1&source=full&prefix=https://my-proxy.com/?url=
```

---   
  
</details>

<details>
<summary>🛠️ 参数说明</summary>
  
# 
  
| 参数     | 说明             | 可选值                          | 示例         |        
| -------- | ---------------- | ------------------------------- | ------------ |
| `url`    | 代理任意 API 请求 | 任意有效 URL                     | `?url=https://...` |
| `format` | 配置模式         | `0 或 raw = 原始 JSON`  `1 或 proxy = 添加代理前缀`  `2 或 base58 = 原始 Base58`  `3 或 proxy-base58 = 代理 Base58` | `?format=0` |
| `source` | 配置源选择       | `jin18` = 精简版`jingjian` = 精简+成人`full` = 完整版） | `?source=jin18` |
| `prefix` | 自定义代理前缀   | 任意代理地址                      | `?prefix=https://.../?url=` |
| `errors&limit=10` | 查看错误日志 | `errors&limit=10`                 | `https://<你的域名>?errors&limit=10` |

---  

## 📦 配置源对比

| 配置源 | 资源数量 | 包含成人内容 | 适用场景 |
| --- | --- | --- | --- |
| **jin18** | 31个 | ❌ 否 | 家庭使用、轻量级应用 |
| **jingjian** | 61个 | ✅ 是 | 个人使用、中等需求 |
| **full** | 88个 | ✅ 是 | 完整功能、最大兼容性 |


🧩 **前缀替换逻辑**  
- 若 JSON 中的 `api` 字段已包含旧前缀（`?url=`），系统会自动去除旧前缀并替换为新的代理前缀。  
- 可自定义代理路径，方便接入私有 API 或多 Worker 配置。
  
---   
  
</details>

<details>
<summary> 📋 完整订阅链接模板</summary>
  
# 

将 `\<你的域名\>` 替换为你的实际 Worker 地址：

### 精简版（jin18）

```jsx
# 原始 JSON
https://<你的域名>/?format=0&source=jin18

# 带代理前缀的 JSON
https://<你的域名>/?format=1&source=jin18

# 原始 Base58 编码
https://<你的域名>/?format=2&source=jin18

# 代理 Base58 编码（推荐用于订阅）
https://<你的域名>/?format=3&source=jin18
```

### 精简+成人版（jingjian）

```jsx
# 原始 JSON
https://<你的域名>/?format=0&source=jingjian

# 带代理前缀的 JSON
https://<你的域名>/?format=1&source=jingjian

# 原始 Base58 编码
https://<你的域名>/?format=2&source=jingjian

# 代理 Base58 编码（推荐用于订阅）
https://<你的域名>/?format=3&source=jingjian
```

### 完整版（full，默认）

```jsx
# 原始 JSON
https://<你的域名>/?format=0&source=full

# 带代理前缀的 JSON
https://<你的域名>/?format=1&source=full

# 原始 Base58 编码
https://<你的域名>/?format=2&source=full

# 代理 Base58 编码（推荐用于订阅）
https://<你的域名>/?format=3&source=full
```

---   

</details>

<details>
<summary>📌 注意事项</summary>
  
# 
  
- **Workers 免费额度**：每天 10 万次请求，适合轻量使用。超出后需升级付费套餐。
- **代理替换逻辑**：如果 JSON 中 `api` 字段已包含 `?url=` 前缀，会先去掉旧前缀，再加上新前缀。
- **Base58 输出**：适合直接作为订阅链接在支持该格式的客户端中使用。
- **配置源更新**：配置源来自 GitHub，内容会定期更新。Worker 会缓存 7200 秒（2小时）。
- **超时设置**：默认请求超时时间为 9 秒，超时后会返回错误信息。
- **CORS 支持**：已启用完整的 CORS 支持，可直接在前端应用中调用。

---   
  
</details>

<details>
<summary>🔧 高级配置</summary>
  
# 

### 修改配置源地址

在 `worker.js` 中找到 `JSON_SOURCES` 对象并修改：

```jsx
const JSON_SOURCES = {
  'jin18': 'https://raw.githubusercontent.com/your-repo/jin18.json',
  'jingjian': 'https://raw.githubusercontent.com/your-repo/jingjian.json',
  'full': 'https://raw.githubusercontent.com/your-repo/full.json'
}
```

### 修改超时时间

找到以下代码并修改超时毫秒数：

```jsx
const timeoutId = setTimeout(() => controller.abort(), 9000) // 改为其他值
```

### 添加访问日志

可以在代码中添加日志记录：

```jsx
console.log(`Request from: ${request.headers.get('cf-connecting-ip')}`)
```

</details>

---

## 🆕 更新内容

- 📄 **Luna-TV配置编辑器**：专业的 JSON 配置文件可视化编辑器。  
- 🔍 **自动检测API状态**：每 1 小时检测一次 API 可用性，并记录最近 100 次测试报告。  
- 🧩 **源名称前添加图标**：源名称前添加图标，方便区分。  
- 🌐 **被墙资源自动中转**：为受限 API 提供 CF Worker 中转能力。  
  
---   

## 🧪 测试与示例

### ✅ 使用中转API测试
- 通过 CORSAPI 转发后，大幅提升视频源可用率。  
- 可“复活”原本无法访问的资源。  

### ⚙️ 精简版源更新
- 去除污染源与无搜索结果源（如 🎬虎牙、🔞丝袜、🔞色猫）。  
- 精简后共 **57 个可用源**，在中转代理下全部可访问。  
<details>
<summary>示例</summary>
<img width="1025" height="486" alt="61" src="https://github.com/user-attachments/assets/81c80108-7c03-4583-87ab-b7b57cdfd3bd" />
  
  
</details>

---   
  
# API 健康报告（每日自动检测API状态）

## API 状态（最近更新：2026-04-24 02:06 CST）

- 总 API 数量：79
- 成功 API 数量：66
- 失败 API 数量：13
- 平均可用率：79.2%
- 完美可用率（100%）：0 个
- 高可用率（80%-99%）：48 个
- 中等可用率（50%-79%）：25 个
- 低可用率（<50%）：6 个

<div style="font-size: 11px;">

<!-- API_TABLE_START -->
| 状态 | 资源名称 | 地址 | 采集接口 | 成功次数 | 失败次数 | 可用率 | 连续失败 | 最近7天趋势 |
|------|---------|------|---------|----------:|----------:|--------:|-----------:|--------------|
| ✅ | 🎬-爱奇艺- | [🔗](https://iqiyizyapi.com) | [iqiyizyapi.com](https://iqiyizyapi.com/api.php/provide/vod "点击访问完整 API") | 99 | 1 | 99.0% | 0 | ✅✅✅✅✅✅✅ |
| ✅ | 🎬iKun资源 | [🔗](https://ikunzy.com) | [ikunzyapi.com](https://ikunzyapi.com/api.php/provide/vod "点击访问完整 API") | 99 | 1 | 99.0% | 0 | ✅✅✅✅✅✅✅ |
| ✅ | 🎬最大点播 | [🔗](https://zuidazy.co) | [zuidazy.me](https://zuidazy.me/api.php/provide/vod "点击访问完整 API") | 99 | 1 | 99.0% | 0 | ✅✅✅✅✅✅✅ |
| ✅ | 🎬建安资源 | [🔗](http://154.219.117.232:9981) | [154.219.117.232](http://154.219.117.232:9981/jacloudapi.php/provide/vod "点击访问完整 API") | 99 | 1 | 99.0% | 0 | ✅✅✅✅✅✅✅ |
| ✅ | 🎬无尽资源 | [🔗](https://wujinzy.com) | [api.wujinapi.me](https://api.wujinapi.me/api.php/provide/vod "点击访问完整 API") | 99 | 1 | 99.0% | 0 | ✅✅✅✅✅✅✅ |
| ✅ | 🎬暴风资源 | [🔗](https://bfzy.tv) | [bfzyapi.com](https://bfzyapi.com/api.php/provide/vod "点击访问完整 API") | 99 | 1 | 99.0% | 0 | ✅✅✅✅✅✅✅ |
| ✅ | 🎬红牛资源 | [🔗](https://www.hongniuzy.com) | [hongniuzy2.com](https://www.hongniuzy2.com/api.php/provide/vod "点击访问完整 API") | 99 | 1 | 99.0% | 0 | ✅✅✅✅✅✅✅ |
| ✅ | 🎬速播资源 | [🔗](https://www.subozy.com) | [subocaiji.com](https://subocaiji.com/api.php/provide/vod "点击访问完整 API") | 99 | 1 | 99.0% | 0 | ✅✅✅✅✅✅✅ |
| ✅ | 🎬量子影视 | [🔗](https://lzizy.net) | [cj.lziapi.com](https://cj.lziapi.com/api.php/provide/vod "点击访问完整 API") | 99 | 1 | 99.0% | 0 | ✅✅✅✅✅✅✅ |
| ✅ | 🎬量子资源 | [🔗](https://cj.lzcaiji.com) | [cj.lzcaiji.com](https://cj.lzcaiji.com/api.php/provide/vod "点击访问完整 API") | 99 | 1 | 99.0% | 0 | ✅✅✅✅✅✅✅ |
| ✅ | 🎬360 资源 | [🔗](https://360zy.com) | [360zy.com](https://360zy.com/api.php/provide/vod "点击访问完整 API") | 98 | 2 | 98.0% | 0 | ✅✅✅✅✅✅✅ |
| ✅ | 🎬光速资源 | [🔗](https://api.guangsuapi.com) | [api.guangsuapi.com](https://api.guangsuapi.com/api.php/provide/vod "点击访问完整 API") | 98 | 2 | 98.0% | 0 | ✅✅✅✅✅✅✅ |
| ✅ | 🎬最大资源 | [🔗](https://zuida.xyz) | [api.zuidapi.com](https://api.zuidapi.com/api.php/provide/vod "点击访问完整 API") | 98 | 2 | 98.0% | 0 | ✅✅✅✅✅✅✅ |
| ✅ | 🎬卧龙影视 | [🔗](https://collect.wolongzyw.com) | [collect.wolongzyw.com](https://collect.wolongzyw.com/api.php/provide/vod "点击访问完整 API") | 98 | 2 | 98.0% | 0 | ✅✅✅✅✅✅✅ |
| ✅ | 🎬卧龙资源 | [🔗](https://wolongzyw.com) | [wolongzyw.com](https://wolongzyw.com/api.php/provide/vod "点击访问完整 API") | 98 | 2 | 98.0% | 0 | ✅✅✅✅✅✅✅ |
| ✅ | 🎬新浪资源 | [🔗](https://xinlangapi.com) | [api.xinlangapi.com](https://api.xinlangapi.com/xinlangapi.php/provide/vod "点击访问完整 API") | 98 | 2 | 98.0% | 0 | ✅✅✅✅✅✅✅ |
| ✅ | 🎬无尽影视 | [🔗](https://wujinzy.com) | [api.wujinapi.com](https://api.wujinapi.com/api.php/provide/vod "点击访问完整 API") | 98 | 2 | 98.0% | 0 | ✅✅✅✅✅✅✅ |
| ✅ | 🎬旺旺短剧 | [🔗](https://wwzy.tv) | [wwzy.tv](https://wwzy.tv/api.php/provide/vod "点击访问完整 API") | 98 | 2 | 98.0% | 0 | ✅✅✅✅✅✅✅ |
| ✅ | 🎬旺旺资源 | [🔗](https://api.wwzy.tv) | [api.wwzy.tv](https://api.wwzy.tv/api.php/provide/vod "点击访问完整 API") | 98 | 2 | 98.0% | 0 | ✅✅✅✅✅✅✅ |
| ✅ | 🎬极速资源 | [🔗](https://jszyapi.com) | [jszyapi.com](https://jszyapi.com/api.php/provide/vod "点击访问完整 API") | 98 | 2 | 98.0% | 0 | ✅✅✅✅✅✅✅ |
| ✅ | 🎬电影天堂 | [🔗](http://caiji.dyttzyapi.com) | [caiji.dyttzyapi.com](http://caiji.dyttzyapi.com/api.php/provide/vod "点击访问完整 API") | 98 | 2 | 98.0% | 0 | ✅✅✅✅✅✅✅ |
| ✅ | 🎬豆瓣资源 | [🔗](https://dbzy.tv) | [caiji.dbzy5.com](https://caiji.dbzy5.com/api.php/provide/vod "点击访问完整 API") | 98 | 2 | 98.0% | 0 | ✅✅✅✅✅✅✅ |
| ❌ | 🎬金鹰点播 | [🔗](https://jinyingzy.com) | [jinyingzy.com](https://jinyingzy.com/api.php/provide/vod "点击访问完整 API") | 98 | 2 | 98.0% | 1 | ✅✅✅✅✅✅❌ |
| ✅ | 🎬天涯影视 | [🔗](https://tyyszy.com) | [tyyszy.com](https://tyyszy.com/api.php/provide/vod "点击访问完整 API") | 97 | 3 | 97.0% | 0 | ✅✅✅✅✅✅✅ |
| ✅ | 🎬非凡资源 | [🔗](https://cj.ffzyapi.com) | [api.ffzyapi.com](https://api.ffzyapi.com/api.php/provide/vod "点击访问完整 API") | 97 | 3 | 97.0% | 0 | ✅✅✅✅✅✅✅ |
| ✅ | 🎬飘零资源 | [🔗](https://p2100.net) | [p2100.net](https://p2100.net/api.php/provide/vod "点击访问完整 API") | 97 | 3 | 97.0% | 0 | ✅✅✅✅✅✅✅ |
| ✅ | 🎬魔都动漫 | [🔗](https://caiji.moduapi.cc) | [caiji.moduapi.cc](https://caiji.moduapi.cc/api.php/provide/vod "点击访问完整 API") | 95 | 5 | 95.0% | 0 | ❌✅✅✅✅✅✅ |
| ❌ | 🎬猫眼资源 | [🔗](https://www.maoyanzy.com) | [api.maoyanapi.top](https://api.maoyanapi.top/api.php/provide/vod "点击访问完整 API") | 94 | 6 | 94.0% | 1 | ✅❌✅✅✅✅❌ |
| ✅ | 🎬茅台资源 | [🔗](https://mtzy.me) | [caiji.maotaizy.cc](https://caiji.maotaizy.cc/api.php/provide/vod "点击访问完整 API") | 94 | 6 | 94.0% | 0 | ✅✅✅✅✅✅✅ |
| ✅ | 🎬魔都资源 | [🔗](https://www.moduzy.net) | [mdzyapi.com](https://www.mdzyapi.com/api.php/provide/vod "点击访问完整 API") | 94 | 6 | 94.0% | 0 | ✅✅✅✅✅✅✅ |
| ✅ | 🎬U酷影视 | [🔗](https://www.ukuzy.com) | [api.ukuapi88.com](https://api.ukuapi88.com/api.php/provide/vod "点击访问完整 API") | 91 | 9 | 91.0% | 0 | ✅✅✅✅✅✅✅ |
| ✅ | 🎬快车资源 | [🔗](https://kuaichezy.com) | [caiji.kuaichezy.org](https://caiji.kuaichezy.org/api.php/provide/vod "点击访问完整 API") | 87 | 13 | 87.0% | 0 | ❌✅✅✅✅✅✅ |
| ✅ | 🎬索尼资源 | [🔗](https://suonizy.net) | [suoniapi.com](https://suoniapi.com/api.php/provide/vod "点击访问完整 API") | 86 | 14 | 86.0% | 0 | ❌✅✅✅✅✅✅ |
| ✅ | 🎬虎牙资源 | [🔗](https://www.huyaapi.com) | [huyaapi.com](https://www.huyaapi.com/api.php/provide/vod "点击访问完整 API") | 86 | 14 | 86.0% | 0 | ❌✅✅✅✅✅✅ |
| ✅ | 🎬鸭鸭资源 | [🔗](https://yayazy3.com) | [cj.yayazy.net](https://cj.yayazy.net/api.php/provide/vod "点击访问完整 API") | 86 | 14 | 86.0% | 0 | ❌✅✅✅✅✅✅ |
| ✅ | 🔞155-资源 | [🔗](https://155zy2.com) | [155api.com](https://155api.com/api.php/provide/vod "点击访问完整 API") | 86 | 14 | 86.0% | 0 | ❌✅✅✅✅✅✅ |
| ✅ | 🎬樱花资源 | [🔗](https://yhzy.cc) | [m3u8.apiyhzy.com](https://m3u8.apiyhzy.com/api.php/provide/vod "点击访问完整 API") | 85 | 15 | 85.0% | 0 | ❌✅✅✅✅✅✅ |
| ✅ | 🎬闪电资源 | [🔗](https://shandianzy.com) | [xsd.sdzyapi.com](https://xsd.sdzyapi.com/api.php/provide/vod "点击访问完整 API") | 85 | 15 | 85.0% | 0 | ❌✅✅✅✅✅✅ |
| ✅ | 🔞玉兔资源 | [🔗](https://apiyutu.com) | [apiyutu.com](https://apiyutu.com/api.php/provide/vod "点击访问完整 API") | 84 | 16 | 84.0% | 0 | ❌❌✅✅✅✅✅ |
| ✅ | 🔞百万资源 | [🔗](https://api.bwzym3u8.com) | [api.bwzyz.com](https://api.bwzyz.com/api.php/provide/vod "点击访问完整 API") | 83 | 17 | 83.0% | 0 | ❌✅✅✅✅✅✅ |
| ✅ | 🔞精品资源 | [🔗](https://www.jingpinx.com) | [jingpinx.com](https://www.jingpinx.com/api.php/provide/vod "点击访问完整 API") | 83 | 17 | 83.0% | 0 | ❌✅✅✅✅✅✅ |
| ✅ | 🔞jkun资源 | [🔗](https://jkunzyapi.com) | [jkunzyapi.com](https://jkunzyapi.com/api.php/provide/vod "点击访问完整 API") | 82 | 18 | 82.0% | 0 | ❌✅✅✅✅✅✅ |
| ✅ | 🔞番号资源 | [🔗](http://fhapi9.com) | [fhapi9.com](http://fhapi9.com/api.php/provide/vod "点击访问完整 API") | 82 | 18 | 82.0% | 0 | ❌✅✅✅✅✅✅ |
| ✅ | 🔞-老色逼- | [🔗](https://apilsbzy1.com) | [apilsbzy1.com](https://apilsbzy1.com/api.php/provide/vod "点击访问完整 API") | 81 | 19 | 81.0% | 0 | ❌❌✅✅✅✅✅ |
| ✅ | 🔞小鸡资源 | [🔗](https://xiaojizy.live) | [api.xiaojizy.live](https://api.xiaojizy.live/provide/vod "点击访问完整 API") | 81 | 19 | 81.0% | 0 | ❌✅✅✅✅✅✅ |
| ✅ | 🎬优质资源 | [🔗](https://1080zyk4.com) | [api.yzzy-api.com](https://api.yzzy-api.com/inc/apijson.php "点击访问完整 API") | 80 | 20 | 80.0% | 0 | ❌✅✅✅✅✅✅ |
| ✅ | 🔞--AIvin- | [🔗](http://lbapiby.com) | [lbapiby.com](http://lbapiby.com/api.php/provide/vod "点击访问完整 API") | 80 | 20 | 80.0% | 0 | ❌❌✅✅✅✅✅ |
| ✅ | 🔞-大奶子- | [🔗](https://apidanaizi.com) | [apidanaizi.com](https://apidanaizi.com/api.php/provide/vod "点击访问完整 API") | 80 | 20 | 80.0% | 0 | ❌❌✅✅✅✅✅ |
| ✅ | 🔞乐播资源 | [🔗](https://lbapi9.com) | [lbapi9.com](https://lbapi9.com/api.php/provide/vod "点击访问完整 API") | 79 | 21 | 79.0% | 0 | ❌❌✅✅✅✅✅ |
| ✅ | 🔞桃花资源 | [🔗](https://thzy8.me) | [thzy1.me](https://thzy1.me/api.php/provide/vod "点击访问完整 API") | 79 | 21 | 79.0% | 0 | ❌❌✅✅✅✅✅ |
| ✅ | 🔞辣椒资源 | [🔗](https://apilj.com) | [apilj.com](https://apilj.com/api.php/provide/vod "点击访问完整 API") | 78 | 22 | 78.0% | 0 | ❌❌✅✅✅✅✅ |
| ✅ | 🔞森林资源 | [🔗](https://slapibf.com) | [beiyong.slapibf.com](https://beiyong.slapibf.com/api.php/provide/vod "点击访问完整 API") | 77 | 23 | 77.0% | 0 | ❌❌✅✅✅✅✅ |
| ✅ | 🔞滴滴资源 | [🔗](https://didizy.com) | [api.ddapi.cc](https://api.ddapi.cc/api.php/provide/vod "点击访问完整 API") | 77 | 23 | 77.0% | 0 | ❌❌✅✅✅✅✅ |
| ✅ | 🔞鲨鱼资源 | [🔗](https://shayuapi.com) | [shayuapi.com](https://shayuapi.com/api.php/provide/vod "点击访问完整 API") | 77 | 23 | 77.0% | 0 | ❌❌✅✅✅✅✅ |
| ✅ | 🔞 CK-资源 | [🔗](https://ckzy.me) | [ckzy.me](https://ckzy.me/api.php/provide/vod "点击访问完整 API") | 76 | 24 | 76.0% | 0 | ❌❌✅✅✅✅✅ |
| ✅ | 🔞黄色仓库 | [🔗](https://hsckzy.xyz) | [hsckzy.xyz](https://hsckzy.xyz/api.php/provide/vod "点击访问完整 API") | 76 | 24 | 76.0% | 0 | ❌✅✅✅✅✅✅ |
| ✅ | 🔞白嫖资源 | [🔗](https://www.kxgav.com) | [kxgav.com](https://www.kxgav.com/api/json.php "点击访问完整 API") | 75 | 25 | 75.0% | 0 | ❌❌✅✅✅✅✅ |
| ✅ | 🔞香蕉资源 | [🔗](https://www.xiangjiaozyw.com) | [xiangjiaozyw.com](https://www.xiangjiaozyw.com/api.php/provide/vod "点击访问完整 API") | 75 | 25 | 75.0% | 0 | ❌❌✅✅✅✅✅ |
| ✅ | 🔞-美少女- | [🔗](https://www.msnii.com) | [msnii.com](https://www.msnii.com/api/json.php "点击访问完整 API") | 74 | 26 | 74.0% | 0 | ❌❌✅✅✅✅✅ |
| ✅ | 🔞细胞资源 | [🔗](https://www.xxibaozyw.com) | [xxibaozyw.com](https://www.xxibaozyw.com/api.php/provide/vod "点击访问完整 API") | 74 | 26 | 74.0% | 0 | ❌❌✅✅✅✅✅ |
| ✅ | 🔞-黄AVZY | [🔗](https://www.pgxdy.com) | [pgxdy.com](https://www.pgxdy.com/api/json.php "点击访问完整 API") | 73 | 27 | 73.0% | 0 | ❌❌✅✅✅✅✅ |
| ✅ | 🔞奶香资源 | [🔗](https://Naixxzy.com) | [naixxzy.com](https://Naixxzy.com/api.php/provide/vod "点击访问完整 API") | 73 | 27 | 73.0% | 0 | ❌❌✅✅✅✅✅ |
| ✅ | 🔞色猫资源 | [🔗](https://semaozy1.com) | [caiji.semaozy.net](https://caiji.semaozy.net/inc/apijson_vod.php/provide/vod "点击访问完整 API") | 73 | 27 | 73.0% | 0 | ❌❌✅✅✅✅✅ |
| ✅ | 🔞丝袜资源 | [🔗](https://siwazyw.tv) | [siwazyw.tv](https://siwazyw.tv/api.php/provide/vod "点击访问完整 API") | 72 | 28 | 72.0% | 0 | ❌❌✅✅✅✅✅ |
| ✅ | 🔞大地资源 | [🔗](https://dadizy11.com) | [dadiapi.com](https://dadiapi.com/feifei "点击访问完整 API") | 72 | 28 | 72.0% | 0 | ❌❌✅✅✅✅✅ |
| ✅ | 🔞麻豆视频 | [🔗](https://91md.me) | [91md.me](https://91md.me/api.php/provide/vod "点击访问完整 API") | 70 | 30 | 70.0% | 0 | ❌✅✅✅✅✅✅ |
| ✅ | 🔞豆豆资源 | [🔗](https://doudouzy.com) | [api.douapi.cc](https://api.douapi.cc/api.php/provide/vod "点击访问完整 API") | 67 | 33 | 67.0% | 0 | ❌❌✅✅✅✅✅ |
| 🚨 | 🎬豪华资源 | [🔗](https://www.haohuazy.com) | [pz.168188.dpdns.org](https://pz.168188.dpdns.org/?url=https://hhzyapi.com/api.php/provide/vod "点击访问完整 API") | 66 | 34 | 66.0% | 25 | ❌❌❌❌❌❌❌ |
| 🚨 | 🎬百度云zy | [🔗](https://bdzy1.com) | [pz.168188.dpdns.org](https://pz.168188.dpdns.org/?url=https://api.apibdzy.com/api.php/provide/vod "点击访问完整 API") | 65 | 35 | 65.0% | 25 | ❌❌❌❌❌❌❌ |
| ✅ | 🔞-奥斯卡- | [🔗](https://aosikazy.com) | [aosikazy.com](https://aosikazy.com/api.php/provide/vod "点击访问完整 API") | 61 | 39 | 61.0% | 0 | ❌❌✅✅✅✅✅ |
| 🚨 | 🎬如意资源 | [🔗](https://www.ryzyw.com) | [pz.168188.dpdns.org](https://pz.168188.dpdns.org/?url=https://cj.rycjapi.com/api.php/provide/vod "点击访问完整 API") | 60 | 40 | 60.0% | 25 | ❌❌❌❌❌❌❌ |
| 🚨 | 🔞优优资源 | [🔗](https://www.yyzywcj.com) | [yyzywcj.com](https://www.yyzywcj.com/api.php/provide/vod "点击访问完整 API") | 60 | 40 | 60.0% | 24 | ❌❌❌❌❌❌❌ |
| 🚨 | 🔞杏吧资源 | [🔗](https://xingba111.com) | [pz.168188.dpdns.org](https://pz.168188.dpdns.org/?url=https://xingba222.com/api.php/provide/vod "点击访问完整 API") | 56 | 44 | 56.0% | 25 | ❌❌❌❌❌❌❌ |
| 🚨 | 🔞-幸资源- | [🔗](https://xzytv.com) | [xzybb2.com](https://xzybb2.com/api.php/provide/vod "点击访问完整 API") | 17 | 83 | 17.0% | 62 | ❌❌❌❌❌❌❌ |
| 🚨 | 🔞91-精品- | [🔗](https://91jpzyw.com) | [91jpzyw.com](https://91jpzyw.com/api.php/provide/vod "点击访问完整 API") | 11 | 89 | 11.0% | 86 | ❌❌❌❌❌❌❌ |
| 🚨 | 🎬山海资源 | [🔗](https://zy.sh0o.cn) | [zy.sh0o.cn](https://zy.sh0o.cn/api.php/provide/vod "点击访问完整 API") | 3 | 97 | 3.0% | 96 | ❌❌❌❌❌❌❌ |
| 🚨 | 🔞最色资源 | [🔗](https://zuisezy.com) | [api.zuiseapi.com](https://api.zuiseapi.com/api.php/provide/vod "点击访问完整 API") | 1 | 99 | 1.0% | 69 | ❌❌❌❌❌❌❌ |
| 🚨 | 🔞-色南国- | [🔗](https://api.sexnguon.com) | [api.sexnguon.com](https://api.sexnguon.com/api.php/provide/vod "点击访问完整 API") | 0 | 100 | 0.0% | 100 | ❌❌❌❌❌❌❌ |
| 🚨 | 🔞souavZY | [🔗](https://api.souavzy.vip) | [api.souavzy.vip](https://api.souavzy.vip/api.php/provide/vod "点击访问完整 API") | 0 | 100 | 0.0% | 100 | ❌❌❌❌❌❌❌ |
<!-- API_TABLE_END -->























































































































































































