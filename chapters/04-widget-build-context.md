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

## 为什么 `build` 会反复执行

初学者很容易误以为 `build` 只会执行一次。

其实很多情况下，界面变化后会重新执行 `build`，比如：

- 调用了 `setState`
- 父组件重建了
- 依赖的状态变化了

所以要养成一个习惯：

- `build` 里主要负责“描述界面”
- 不要在 `build` 里做重副作用逻辑

## `context` 最容易踩的一个点

很多 Flutter API 都需要 `context`，但它不是随便哪个位置都能用。

比如你常会看到：

```dart
Navigator.of(context).push(...);
Theme.of(context);
```

可以先记住：

- `context` 总是和当前 Widget 所在位置有关
- 它越像“树上的当前位置”，你越容易理解很多 API 为什么依赖它
