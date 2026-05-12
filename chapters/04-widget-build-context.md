# 04 补充：Widget、build、BuildContext

对应主文档章节：`4. Widget、build、BuildContext`

## Widget 是什么

Widget 可以理解成“界面的描述对象”。

- `Text` 描述文字
- `Row` 描述横向布局
- `Scaffold` 描述页面骨架

## `build` 在做什么

`build` 的职责很简单：返回当前这次要显示的界面。

```dart
@override
Widget build(BuildContext context) {
  return const Text('Hello');
}
```

## `BuildContext` 怎么理解

可以先把它理解成“当前 Widget 在界面树中的位置凭证”。

它常用来做这些事：

- 找主题 `Theme.of(context)`
- 找路由 `Navigator.of(context)`
- 找媒体信息 `MediaQuery.of(context)`

## 初学者先记住

`context` 不是页面对象，它更像“当前位置的上下文入口”。
