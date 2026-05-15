# 07 补充：MaterialApp、Scaffold、AppBar

对应主文档章节：`7. MaterialApp、Scaffold、AppBar`

## `MaterialApp`

通常是应用级总入口，常见配置有：

- `home`
- `theme`
- `routes`
- `debugShowCheckedModeBanner`

## `Scaffold`

通常是单个页面的骨架，常见区域有：

- `appBar`
- `body`
- `bottomNavigationBar`
- `floatingActionButton`

## `AppBar`

负责页面顶部导航区域，常见内容有：

- 标题
- 返回按钮
- 右侧操作按钮

## 一个阅读顺序

看页面文件时，先找 `Scaffold`，再看 `appBar` 和 `body`，通常能很快明白页面结构。

## 一个最常见的页面骨架

```dart
Scaffold(
  appBar: AppBar(
    title: const Text('Home'),
  ),
  body: const SizedBox(),
  floatingActionButton: FloatingActionButton(
    onPressed: null,
    child: Icon(Icons.add),
  ),
)
```

这类结构在 Flutter 页面里非常高频。

## 为什么初学者先学这三个最划算

因为你读大多数页面时，先找到这三层通常就能快速回答：

- 这是哪个页面
- 页面顶部显示什么
- 页面主体内容在哪里

这比一上来钻进最深层的 `child` 更容易抓住整体。
