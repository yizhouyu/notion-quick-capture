# notion-quick-capture

Three-second activity logging to a Notion database from your Android home screen. No server, no middleman — your phone talks straight to the Notion API.

把「我们去了哪/吃了什么」三秒记进 Notion:主屏一键 → 说一句话 → 入库。零服务器,手机直连 Notion API。

## How it works

[HTTP Shortcuts](https://play.google.com/store/apps/details?id=ch.rmy.android.http_shortcuts) (open-source Android app) + a config file ([`couple-log-shortcuts.json`](couple-log-shortcuts.json)) that defines two buttons:

- **🍽 餐厅打卡** — one tap, type/dictate the restaurant name, optional note, done (Tag auto-set to Restaurant)
- **📝 记一笔** — same, plus a single-select tag menu (Outdoors / Travel / Show / …)

Date is auto-filled with today. The Notion token lives only as a **device-local secret variable** — the config file contains no secrets and never exports your token.

## Setup (~5 min)

1. Create a Notion integration at [notion.so/my-integrations](https://www.notion.so/my-integrations) and connect it to **only** the target database (least privilege — the token can't touch anything else)
2. Install HTTP Shortcuts, then import the config — either from URL (raw link of `couple-log-shortcuts.json`) or via this one-tap deep link from your phone:
   `https://http-shortcuts.rmy.ch/import?url=<url-encoded raw link>`
3. In the app: Variables → `notion_token` → paste your token
4. Edit the `database_id` in both shortcuts' request bodies to your own database (schema: `Name` title / `Date` date / `Tags` multi-select / `Comments` rich text)
5. Add the two shortcuts to your home screen

## Staying up to date

In the app, enable **Automatic Import** (merge mode) pointed at the raw config URL — every device pulls config updates automatically. Tokens are unaffected (they're local variables).

---
Built with Claude Code. 🤖
