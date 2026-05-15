# 03 补充：第一个 Flutter 页面

对应主文档章节：`3. 第一个 Flutter 页面`

## 逐层拆开看

```dart
MaterialApp(
  home: Scaffold(
    body: Center(
      child: Text('Hello Flutter'),
    ),
  ),
)
```

这段代码是一个很典型的 Flutter 页面树：

- `MaterialApp`：应用容器
- `Scaffold`：页面骨架
- `Center`：居中布局
- `Text`：具体内容

## 读代码技巧

不要试图一口气读完整棵树。

建议从外往里拆：

1. 最外层负责什么
2. 中间层负责什么
3. 最里层显示什么

## 再看一个稍微真实一点的页面

```dart
Scaffold(
  appBar: AppBar(
    title: const Text('Home'),
  ),
  body: const Center(
    child: Text('Hello Flutter'),
  ),
)
```

这时你就可以继续往下拆：

- `Scaffold`：页面整体框架
- `AppBar`：顶部栏
- `Center`：让内容居中
- `Text`：真正展示的文字

## 初学者最实用的读法

看到页面代码时，先问自己：

- 最外层是哪个组件
- 中间层在做布局还是结构
- 最里层真正显示的是什么

只要先按层拆，Widget 树就不会那么可怕。
