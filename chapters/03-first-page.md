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
