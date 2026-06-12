# notion-quick-capture

我们俩的「What we've done together」三秒记录工具。手机主屏一键 → 入 Notion,零服务器,手机直连 Notion API。

## 一个按钮:记一笔 ✏️

| 入口 | 行为 | Tag |
|------|------|-----|
| Google Maps → Share → HTTP Shortcuts | 零输入,自动抽店名 | 自动 Restaurant |
| 主屏手动点开 | 弹框说一句 | 单选菜单(库里真实用过的 11 个) |

每次提交前有确认弹窗(Cancel 可改内容或放弃);成功后可一键打开刚写入的 Notion 页面;空内容不会写入。

## 安装(每台手机一次,~5 分钟)

1. **装 app**:Play Store 搜 **HTTP Shortcuts**(作者 Waboodoo,开源)
2. **导入配置**:app 主界面右上 ⋮ → Import / Export → **Import from URL**,粘贴:
   ```
   https://raw.githubusercontent.com/yizhouyu/notion-quick-capture/main/couple-log-shortcuts.json
   ```
3. **填 token**:⋮ → Variables → `notion_token` → 粘贴 token(见下方「token 在哪」)
4. **上主屏**:长按 记一笔 → Place on home screen

## Token 在哪 / 忘了怎么办

- Token 是 Notion 的 integration secret(`ntn_` 开头),在 **[notion.so/my-integrations](https://www.notion.so/my-integrations)** → 点开 `quick-capture` 那个 integration → Configuration → **Internal Integration Secret** → Show / Copy
- **忘了或泄露了**:同一页面可以 **Refresh** 生成新 secret(旧的立即作废),然后在两台手机的 app → Variables → `notion_token` 里换成新值
- **第一次建**:New integration → workspace 选书单/数据库所在的那个 → 建完后,去 Notion 里「What we've done together」页面 → 右上 ⋯ → **Connections** → 添加这个 integration(**只连这一个页面**,最小权限:手机丢了也只暴露这一个库)
- 注意:Mac 上 `~/.config/notion/token` 是另一个**全量权限** token(Claude 数据搬运用),和手机这个不是同一个,不要混用

## 改配置 / 更新

配置文件无任何密钥(token 只存在手机本地变量里),改动直接 push 本 repo。手机端:重新 Import from URL(merge 模式,token 不丢);或在 app 里开 **Automatic Import** 指向上面的 URL,以后自动同步。

## Notion 端 schema

数据库 `What we've done together`:`Name`(title)/ `Date`(date,自动今天)/ `Tags`(multi-select)/ `Comments`(rich text,工具不填,要补去 Notion 补)。
