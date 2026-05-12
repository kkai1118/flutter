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
