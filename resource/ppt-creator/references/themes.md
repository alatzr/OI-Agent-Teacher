# 课件主题（themes）

> 从下面选一套，替换 template.html 顶部 `:root` 里的 CSS 变量。
> **不允许自定义 hex 值**——预设是为了保证投影仪可读性和审美克制。

## 如何切换

把 template.html 的 `:root{...}` 整块替换成目标主题的变量即可，其余样式不动。

---

## T1 靛蓝经典（默认）

沉稳，适合知识点讲义和课堂教案。

```css
:root{
  --bg:#fafaf7; --ink:#1a1a1a; --muted:#6b6b6b; --line:#e2e0d8;
  --accent:#2f5d8a; --accent-soft:#eaf1f7;
  --code-bg:#1e2230; --code-fg:#e6e6e6;
  --ok:#2e7d4f; --warn:#b8741a; --bad:#b8341a;
}
```

## T2 墨绿学术

护眼，长时复习串讲不易疲劳。

```css
:root{
  --bg:#f6f7f3; --ink:#1b2417; --muted:#5c6b52; --line:#dfe3d6;
  --accent:#3c6b3f; --accent-soft:#eaf2e8;
  --code-bg:#1b201a; --code-fg:#e6ece2;
  --ok:#2e7d4f; --warn:#9a6a16; --bad:#a8331a;
}
```

## T3 暖纸黑板

米黄底偏暖，入门组课堂更亲切。

```css
:root{
  --bg:#f7f2e8; --ink:#2a2418; --muted:#7a6f55; --line:#e6dcc4;
  --accent:#8a5a2f; --accent-soft:#f3ead9;
  --code-bg:#241f17; --code-fg:#ede4d2;
  --ok:#3a6b3f; --warn:#9a6a16; --bad:#a8331a;
}
```

## T4 深色演示（暗室/大屏）

深底，强光环境或晚间演示。

```css
:root{
  --bg:#15171c; --ink:#eaeaea; --muted:#9aa0aa; --line:#2c2f38;
  --accent:#6fb3e0; --accent-soft:#1d2a35;
  --code-bg:#0f1116; --code-fg:#e6e6e6;
  --ok:#5ec27a; --warn:#d6a14a; --bad:#e06a5a;
}
.card{background:#1d2027;}
.note{background:#232730; color:#e0e0e0;}
.step,.cover .meta,.hud{color:var(--muted);}
```
> 深色主题下 `.card`/`.note` 需加深背景，已补在变量块后。

---

## 选择建议

| 场景 | 推荐 |
|------|------|
| 知识点讲义 / 课堂教案 | T1 靛蓝经典 |
| 复习串讲（长时） | T2 墨绿学术 |
| 入门组课堂 | T3 暖纸黑板 |
| 暗室 / 晚间 / 强光大屏 | T4 深色演示 |

## 配色纪律

- 强调一律用 `--accent`，不要在正文里随手写别的颜色
- `.note` 三色（黄/绿/红）只在提示框用，不当装饰
- 投影仪实测：浅底主题首选，纯白背景太刺眼，T1 的 `#fafaf7` 是经验值
