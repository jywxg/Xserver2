# 🎮 XServer Game 自动续期

自动为 XServer Game 免费计划续期，防止到期。

---

## 🔄 运行逻辑

```
登录账号 → 跳转游戏面板 → 检查剩余时间
    ├─ ≥ 16小时 → ⌛ 跳过
    └─ < 16小时 → 🔄 执行续期 → 📨 TG 通知
```

---

## 🐙 GitHub Actions 配置

每天 UTC 01:00 自动运行，也可手动触发。

**仓库结构：**

```
📦 公库  ──  存放 workflow yml（.github/workflows/renew.yml）
📦 私库  ──  存放脚本 xserver_game_renew.py（运行时由 Token 拉取）
```

**在公库 `Settings → Secrets → Actions` 中添加：**

| Secret | 必填 | 说明 |
|--------|------|------|
| `PRIVATE_REPO_TOKEN` | ✅ | 有私库读取权限的 GitHub Token |
| `XSERVER_GAME_ACCOUNT` | ✅ | XServer 账号密码，逗号分隔：`foo@gmail.com,pass` |
| `TG_BOT` | ➖ | TG 推送，格式：`chat_id,bot_token` |
| `GOST_PROXY` | ➖ | 代理地址，不填则直连 |

---

## 🔑 GitHub Token 获取

1. 打开 [github.com/settings/tokens](https://github.com/settings/tokens)
2. 点击 **Generate new token (classic)**
3. 勾选权限 `repo`
4. 生成后复制，填入公库 Secrets，命名为 `PRIVATE_REPO_TOKEN`

> ⚠️ Token 只显示一次，请立即保存！

---

## 📨 TG 通知格式

```
🎮 XServer Game 续期通知
🕐 运行时间: 2025-01-01 12:00:00
🖥 服务器: XServer Game 🇯🇵
📅 利用期限: 2025-01-03
📊 续期结果: ✅ 续期成功！
```
