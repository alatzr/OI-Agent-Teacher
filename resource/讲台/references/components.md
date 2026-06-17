# 组件手册（components）

> template.html 内置的组件。出片时直接用对应 HTML 片段，不要自己写样式。

## 1. 代码块（最重要）

OI 课件的代码是主角。严格遵守：

- 用 `<pre class="code">` 包裹，**不要**用 `<code>` 多行——`pre` 才有等宽和背景
- **手动着色**：用 span 类名标注语法，保持简单可读
- 长代码**分页**：一页放不下的逻辑拆成多页，别让滚动条出现

语法着色类：

| 类 | 含义 | 示例 |
|----|------|------|
| `.kw` | 关键字 | int for while if return |
| `.ty` | 类型 | int long vector pair |
| `.st` | 字符串 | "..." |
| `.cm` | 注释 | // 或 /* */ |
| `.fn` | 函数/标识 | 函数名 |
| `.nm` | 数字 | 1 0 -1 1e9 |
| `.hl` | 高亮行 | 整行高亮（重点行） |

**高亮行写法**（整行包 span，注意 margin 负值对齐）：
```html
<pre class="code"><span class="kw">int</span> s = <span class="nm">0</span>;
<span class="hl">s += a[i]; <span class="cm">// ← 这行是重点</span></span>
</pre>
```
> `.hl` 要独占一行，前后不留缩进空格。

**代码块上方加说明**：
```html
<div class="code-cap">prefix_sum.cpp · O(n) 预处理</div>
<pre class="code">...</pre>
```

## 2. 行内代码
```html
<code class="inl">s[r]-s[l-1]</code>
```

## 3. 卡片
```html
<div class="card"><h3>标题</h3><p>内容</p></div>
<div class="card accent"><h3>重点卡</h3><p>左侧带强调色条</p></div>
```

## 4. 步骤流程
```html
<div class="steps">
  <div class="step"><span class="n">1</span><p>选基准</p></div>
  <div class="step"><span class="n">2</span><p>分区</p></div>
  <div class="step"><span class="n">3</span><p>递归</p></div>
</div>
```

## 5. DP/转移表
```html
<table class="grid">
  <tr><th>i</th><th>1</th><th>2</th><th>3</th><th>4</th></tr>
  <tr><th>a[i]</th><td>3</td><td>1</td><td>4</td><td>1</td></tr>
  <tr><th>dp[i]</th><td>3</td><td>4</td><td class="fill">8</td><td class="fill">9</td></tr>
</table>
```
`.fill` 标记当前推导/最终答案格。

## 6. 提示框
```html
<div class="note">普通提示（黄）</div>
<div class="note ok">正确做法（绿）</div>
<div class="note bad">错误/坑（红）</div>
```

## 7. 标签 tag
```html
<span class="tag kw">DP</span>
<span class="tag kw">图论</span>
区分题目标签或知识点分类。
```

## 8. 复杂度/公式
```html
<p class="formula">T(n) = O(n log n)</p>
<span class="big-o">O(n)</span>
```
- 复杂度统一用 `.big-o` 胶囊
- 递推式/数学式用 `.formula`（衬线斜体）

## 9. 页眉 hud
每页（封面、尾页除外）必带，标章节+页码：
```html
<div class="hud"><span class="chap">动态规划</span><span>3 / 12</span></div>
```

## 算法可视化怎么做（重点）

这不是组件，是原则——讲算法一定要有图：

| 算法 | 可视化方式 |
|------|-----------|
| 排序 | `.steps` 放每趟后的数组快照，或 `.grid` 表格画数组变化 |
| DP | `table.grid` 画状态表，`.fill` 标转移路径 |
| BFS/DFS | 用 `.steps` + 文字描述队列/栈状态；节点图可用 SVG（见下） |
| 二分 | `.steps` 标每轮 left/right/mid 的位置 |
| 图论 | 内联 SVG 画节点+边（见示例） |

**SVG 节点图示例**（直接内联在 slide 里）：
```html
<svg width="320" height="180" viewBox="0 0 320 180">
  <line x1="60" y1="90" x2="160" y2="40" stroke="#2f5d8a" stroke-width="2"/>
  <line x1="60" y1="90" x2="160" y2="140" stroke="#2f5d8a" stroke-width="2"/>
  <line x1="160" y1="40" x2="260" y2="90" stroke="#2f5d8a" stroke-width="2"/>
  <circle cx="60" cy="90" r="20" fill="#eaf1f7" stroke="#2f5d8a" stroke-width="2"/>
  <text x="60" y="96" text-anchor="middle" font-size="16">1</text>
  <circle cx="160" cy="40" r="20" fill="#eaf1f7" stroke="#2f5d8a" stroke-width="2"/>
  <text x="160" y="46" text-anchor="middle" font-size="16">2</text>
  <circle cx="160" cy="140" r="20" fill="#eaf1f7" stroke="#2f5d8a" stroke-width="2"/>
  <text x="160" y="146" text-anchor="middle" font-size="16">3</text>
  <circle cx="260" cy="90" r="20" fill="#2f5d8a"/>
  <text x="260" y="96" text-anchor="middle" font-size="16" fill="#fff">4</text>
</svg>
```
SVG 用 `viewBox` 自适应，填色用变量色保持一致。
