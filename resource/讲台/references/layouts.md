# 课件版式骨架（layouts）

> 每页从下面挑一个骨架，套进 template.html 的 `<section class="slide">`。
> 名字对应 CSS 类，照搬结构改文字即可。

## 通用版式

### L1 封面 cover
```html
<section class="slide cover">
  <div class="kicker">OI-Teacher · 课件</div>
  <h1>标题</h1>
  <div class="sub">一句话点题</div>
  <div class="meta">讲者 · 日期 · 组别</div>
</section>
```

### L2 标题+正文（默认）
```html
<section class="slide">
  <div class="hud"><span class="chap">章节</span><span>X / N</span></div>
  <h2>标题</h2>
  <p class="lead">要点</p>
  <ul><li>...</li></ul>
</section>
```

### L3 两栏对比 two-col
左右各一个 card。常用于"朴素做法 vs 优化做法""错误写法 vs 正确写法"。
```html
<section class="slide">
  <div class="hud"><span class="chap">对比</span><span>X/N</span></div>
  <h2>标题</h2>
  <div class="two-col">
    <div class="card"> <h3>左</h3><p>...</p> </div>
    <div class="card accent"> <h3>右</h3><p>...</p> </div>
  </div>
</section>
```

### L4 三栏要点 three-col
```html
<div class="three-col">
  <div class="card"><h3>①</h3><p>...</p></div>
  <div class="card"><h3>②</h3><p>...</p></div>
  <div class="card"><h3>③</h3><p>...</p></div>
</div>
```

### L5 纯代码 code-only
讲算法实现的核心页。代码是主角。
```html
<section class="slide">
  <div class="hud"><span class="chap">代码</span><span>X/N</span></div>
  <h2>核心代码</h2>
  <div class="code-cap">文件名 · 说明</div>
  <pre class="code"> ... </pre>
</section>
```

### L6 步骤流程 steps
排序的分步、BFS 的扩展过程、递归展开。
```html
<div class="steps">
  <div class="step"><span class="n">1</span><p>...</p></div>
  <div class="step"><span class="n">2</span><p>...</p></div>
  <div class="step"><span class="n">3</span><p>...</p></div>
</div>
```

### L7 DP/转移表 grid
用 `table.grid`。手算填表过程、状态转移。
```html
<table class="grid">
  <tr><th>i</th><th>0</th><th>1</th><th>2</th></tr>
  <tr><th>dp[i]</th><td>0</td><td class="fill">3</td><td>5</td></tr>
</table>
```

### L8 提示/坑 note
单独一页强调易错点或关键结论。
```html
<section class="slide">
  <div class="hud"><span class="chap">易错</span><span>X/N</span></div>
  <h2>这个坑别踩</h2>
  <div class="note bad">错误写法：<code class="inl">...</code> —— 原因说明</div>
  <div class="note ok" style="margin-top:16px">正确做法：...</div>
</section>
```

### L9 复杂度/公式 formula
```html
<h2>复杂度分析</h2>
<p class="formula">T(n) = O(n log n)</p>
<p>每次 <span class="big-o">O(log n)</span> × 共 <span class="big-o">n</span> 次</p>
```

### L10 尾页 end
```html
<section class="slide end">
  <h1>小结</h1>
  <div class="quote">核心收束 + 课后行动</div>
</section>
```

## 场景骨架（页面顺序参考）

### 算法知识点讲义
封面 → 为什么学(L2引子) → 概念定义(L2) → 图示/分步(L6或示意) → 代码模板(L5) → 复杂度(L9) → 例题(L2/题面+思路两栏) → 易错(L8) → 小结(L10)

### 题目讲解
封面(题目标题) → 题面(L2) → 数据范围分析(L2,引出复杂度上限) → 思路推演(L6步骤) → 核心代码(L5) → 边界与Hack(L8) → 变式(L3对比) → 小结(L10)

### 复习串讲
封面 → 知识地图(L4三栏分类) → 逐点快览(每点1-2页:定义L2+坑L8) → 易错合集(L4) → 练习指向(L2) → 小结(L10)

### 课堂教案
封面 → 学习目标(L2) → 复习引入(L2) → 新知讲解(L2+L5) → 例题演练(L2/题面→L5代码) → 课堂练习(L2,带小提示) → 总结作业(L10,带时间分配)

> 时间分配写在 hud 或卡片内：如「⏱ 5min」「⏱ 15min」。
