# 15 补充：样式与主题

对应主文档章节：`14. 样式与主题`

## 为什么这章值得单独学

很多初学者一开始能把页面“搭出来”，但页面看起来还是很像默认 demo。

通常差的不是功能，而是这些细节：

- 文字大小和层级
- 间距和留白
- 圆角、边框、背景
- 全局颜色和统一风格

## 先区分：布局和样式

- 布局：组件放哪、怎么排
- 样式：组件看起来怎么样

比如：

- `Row`、`Column` 更偏布局
- `TextStyle`、`BoxDecoration` 更偏样式

## 文字样式：`TextStyle`

```dart
Text(
  'Hello Flutter',
  style: TextStyle(
    fontSize: 18,
    fontWeight: FontWeight.w600,
    color: Colors.black87,
  ),
)
```

初学阶段先掌握这几个最常用属性：

- `fontSize`
- `fontWeight`
- `color`
- `height`

## 间距：`Padding` 和 `SizedBox`

### `Padding`

给子组件留内边距。

```dart
Padding(
  padding: const EdgeInsets.all(16),
  child: Text('Hello'),
)
```

### `SizedBox`

常用来留固定空隙。

```dart
Column(
  children: const [
    Text('Title'),
    SizedBox(height: 12),
    Text('Subtitle'),
  ],
)
```

可以先记：

- 大块留白常想到 `Padding`
- 小间距常想到 `SizedBox`

## 容器样式：`Container` 和 `BoxDecoration`

```dart
Container(
  padding: const EdgeInsets.all(12),
  decoration: BoxDecoration(
    color: Colors.white,
    borderRadius: BorderRadius.circular(12),
    border: Border.all(color: Colors.black12),
    boxShadow: const [
      BoxShadow(
        color: Colors.black12,
        blurRadius: 8,
        offset: Offset(0, 4),
      ),
    ],
  ),
  child: const Text('Card'),
)
```

这里常见的样式能力有：

- 背景色
- 圆角
- 边框
- 阴影

## 主题：`ThemeData`

如果你不想每个页面都重复写颜色和文字风格，就可以放进主题里。

```dart
MaterialApp(
  theme: ThemeData(
    colorSchemeSeed: Colors.blue,
    useMaterial3: true,
  ),
  home: const HomePage(),
)
```

主题的价值是：

- 统一视觉风格
- 减少重复样式代码
- 后面改风格时更集中

## 初学者先建立的样式习惯

- 不要每段文字都随手写不同字号
- 不要页面里到处是随机间距
- 圆角、颜色、边框尽量统一
- 能复用的样式尽量收拢

## 一个最小页面样式思路

如果你现在写一个简单页面，可以先统一这 4 件事：

1. 标题字号
2. 正文字号
3. 页面基础边距
4. 卡片圆角和阴影

只要这 4 件事统一了，页面观感通常就会稳定很多。

## 后面继续学什么

等你把基础样式用顺后，可以再继续看：

- 更完整的 `ThemeData`
- 深色模式
- 自定义组件样式封装
- 设计稿到代码的样式映射
