# Flutter 快速入门

这份文档的目标只有一个：让你能尽快看懂并写出基础 Flutter 页面与交互代码。

建议学习顺序：

1. 先通读一遍
2. 再自己手敲几个页面
3. 最后对照真实项目回看

配套阅读：

- 章节补充目录：`flutter/chapters/README.md`
- Dart 基础文档：`dart/README.md`

这份文档更适合这几类读者：

- 已经学过一点 Dart，准备开始看 Flutter
- 能看懂一点页面代码，但还不清楚整体结构
- 想尽快从“知道组件名字”过渡到“能自己拼页面”

学完这份文档后，你至少应该能做到：

- 看懂一个简单页面的 Widget 树
- 自己写一个带按钮、输入框、列表的小页面
- 看懂最基础的 `setState`、页面跳转、异步加载代码
- 知道后面该往状态管理、网络请求、项目结构哪个方向继续学

## 目录

- [1. Flutter 是什么](#toc-01)
- [2. 开发环境和项目结构](#toc-02)
- [3. 第一个 Flutter 页面](#toc-03)
- [4. Widget、build、BuildContext](#toc-04)
- [5. StatelessWidget 和 StatefulWidget](#toc-05)
- [6. setState 和页面刷新](#toc-06)
- [7. MaterialApp、Scaffold、AppBar](#toc-07)
- [8. 基础布局：Row、Column、Expanded、Container](#toc-08)
- [9. 常用组件：Text、Image、Icon、Button、TextField](#toc-09)
- [10. 列表与滚动](#toc-10)
- [11. 页面跳转与路由](#toc-11)
- [12. 生命周期与异步界面](#toc-12)
- [13. 数据流入门：父子传值与状态提升](#toc-13)
- [14. 样式与主题](#toc-14)
- [15. 调试、常见坑与下一步](#toc-15)

<a id="toc-01"></a>
## 1. Flutter 是什么 · [查看补充](chapters/01-overview.md)

- Flutter 是一个跨平台 UI 框架
- 使用 Dart 编写
- 一套代码可以运行在 iOS、Android、Web、桌面
- 学 Flutter 的关键不是先背组件，而是先理解 Widget、布局、状态、路由

可以先把 Flutter 理解成：用 Dart 直接描述界面树，再由框架把它渲染成真实页面。

<a id="toc-02"></a>
## 2. 开发环境和项目结构 · [查看补充](chapters/02-project-structure.md)

一个最基本的 Flutter 项目，最常接触这些目录和文件：

- `lib/`：主要业务代码
- `main.dart`：应用入口
- `pubspec.yaml`：依赖、资源配置
- `assets/`：图片、字体等资源

入门阶段先学会：能跑起来、知道代码写在哪、知道资源怎么引用。

先别急着研究很复杂的工程分层，入门阶段先把入口、页面、资源、依赖这四块看明白就够了。

<a id="toc-03"></a>
## 3. 第一个 Flutter 页面 · [查看补充](chapters/03-first-page.md)

```dart
import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return const MaterialApp(
      home: Scaffold(
        body: Center(
          child: Text('Hello Flutter'),
        ),
      ),
    );
  }
}
```

先只看这几层：

- `main` 是入口
- `runApp` 启动应用
- `MaterialApp` 是应用壳子
- `Scaffold` 是页面骨架
- `Text` 是具体内容

读这段代码时，不要一口气看完，先按“最外层 -> 中间层 -> 最里层”去拆。

<a id="toc-04"></a>
## 4. Widget、build、BuildContext · [查看补充](chapters/04-widget-build-context.md)

你看到的大多数 Flutter 代码，本质上都在做一件事：

- 组合 Widget
- 在 `build` 里返回界面
- 通过 `BuildContext` 获取当前树中的环境信息

读代码时优先问自己：这个 Widget 负责展示什么，它包了哪些子 Widget。

只要先建立“Flutter 页面本质上是 Widget 树”这个意识，后面很多代码都会突然变得更容易理解。

<a id="toc-05"></a>
## 5. StatelessWidget 和 StatefulWidget · [查看补充](chapters/05-stateless-stateful.md)

区别先记一句话：

- `StatelessWidget`：自己不维护变化状态
- `StatefulWidget`：自己需要维护变化状态

比如：

- 纯标题、纯卡片通常是 `StatelessWidget`
- 计数器、输入框、加载状态页面常是 `StatefulWidget`

初学阶段最实用的判断标准不是“它有没有参数”，而是“它自己会不会变”。

<a id="toc-06"></a>
## 6. setState 和页面刷新 · [查看补充](chapters/06-setstate.md)

```dart
setState(() {
  count++;
});
```

理解重点：

- 改变量不是关键
- 关键是通知 Flutter“状态变了，需要重新 build”
- `setState` 适合入门和局部简单状态

这是理解 Flutter “为什么界面会刷新” 的第一把钥匙。

<a id="toc-07"></a>
## 7. MaterialApp、Scaffold、AppBar · [查看补充](chapters/07-app-shell.md)

这三个通常是你看页面代码时最先遇到的结构：

- `MaterialApp`：应用级配置入口
- `Scaffold`：单页结构骨架
- `AppBar`：页面顶部栏

看项目时，先顺着这条线找页面结构，定位会很快。

很多初学者一看到很长的 Widget 树就乱，其实先抓这三层，通常就已经抓住页面主干了。

<a id="toc-08"></a>
## 8. 基础布局：Row、Column、Expanded、Container · [查看补充](chapters/08-layout-basics.md)

布局入门先抓 4 个：

- `Row`：横向排布
- `Column`：纵向排布
- `Expanded`：占据剩余空间
- `Container`：尺寸、背景、边框、圆角等装饰

大多数布局问题，本质上都跟“父子约束”和“空间怎么分配”有关。

这章是 Flutter 初学最容易卡住、但也最值得尽早搞懂的一章。

<a id="toc-09"></a>
## 9. 常用组件：Text、Image、Icon、Button、TextField · [查看补充](chapters/09-common-widgets.md)

入门时最常写的就是这些：

- 文字：`Text`
- 图片：`Image`
- 图标：`Icon`
- 按钮：`ElevatedButton` / `TextButton`
- 输入框：`TextField`

先掌握它们最基础的属性和常见交互就够了。

如果你只想尽快搭一个能点、能输、能看的页面，先把这几个组件用熟就已经很够用了。

<a id="toc-10"></a>
## 10. 列表与滚动 · [查看补充](chapters/10-scroll-and-list.md)

真实业务页面里，列表和滚动非常高频。

重点先掌握：

- `ListView`
- `ListView.builder`
- `SingleChildScrollView`
- 列表项用 `ListTile` 快速搭起来

真实业务页面里，列表页往往比单页静态布局出现得更多。

<a id="toc-11"></a>
## 11. 页面跳转与路由 · [查看补充](chapters/11-navigation.md)

```dart
Navigator.push(
  context,
  MaterialPageRoute(
    builder: (context) => const DetailPage(),
  ),
);
```

入门阶段先会这两个：

- `Navigator.push`
- `Navigator.pop`

再往后再学统一路由表和命名路由。

入门阶段先掌握“怎么进去、怎么回来、参数怎么带”就够了。

<a id="toc-12"></a>
## 12. 生命周期与异步界面 · [查看补充](chapters/12-lifecycle-and-async.md)

这一章重点是：

- `initState`：初始化时做什么
- `dispose`：销毁前清理什么
- `FutureBuilder`：异步结果回来前后界面怎么切换

很多“页面第一次加载数据”的代码都在这里。

只要你开始接接口、读本地缓存、做延迟加载，这章就会马上变得高频。

<a id="toc-13"></a>
## 13. 数据流入门：父子传值与状态提升 · [查看补充](chapters/13-data-flow.md)

真正写页面时，你很快会遇到：

- 父组件把数据传给子组件
- 子组件通过回调把事件传回去
- 状态该放父组件还是子组件

这就是最基础的数据流思维，也是后面学状态管理的基础。

先把这个模型想清楚，后面学 Provider、Riverpod、Bloc 时就不会只是在背 API。

<a id="toc-14"></a>
## 14. 样式与主题 · [查看补充](chapters/15-styling-and-theme.md)

当你已经能把页面“摆出来”之后，下一步通常就是让它“看起来更像一个真正的页面”。

这章重点先抓这些：

- `TextStyle`：文字大小、字重、颜色
- `Padding` / `SizedBox`：间距和留白
- `Container` / `BoxDecoration`：背景、圆角、边框、阴影
- `ThemeData`：把样式放到全局统一管理

布局解决“放哪”，样式解决“长什么样”，这两者最好分开理解。

<a id="toc-15"></a>
## 15. 调试、常见坑与下一步 · [查看补充](chapters/14-debugging-and-next-steps.md)

入门最常见的问题通常不是语法，而是：

- 布局溢出
- `Expanded` 放错位置
- 列表嵌套导致高度异常
- `setState` 时机不对
- 看不懂报错堆栈

把这些坑踩清楚，上手速度会快很多。

## 建议你学完后立刻做一个最小练习

建议自己写一个小 demo，包含下面 5 个点：

1. 一个 `Scaffold` 页面
2. 一个按钮点击事件
3. 一个 `TextField`
4. 一个 `ListView.builder`
5. 一个 `Navigator.push` 跳转到详情页

如果你能把这个小 demo 独立写出来，说明这份 README 里的主干知识已经真正用起来了。

## 看 Flutter 项目时的推荐顺序

如果你准备从文档过渡到真实项目，建议按这个顺序看：

1. `main.dart`
2. `MaterialApp` 配置
3. 首页或路由入口
4. 页面里的 `Scaffold`
5. 页面中的按钮、输入框、列表、异步逻辑

这样会比“随便点开一个页面文件就硬看”更容易建立整体感。
