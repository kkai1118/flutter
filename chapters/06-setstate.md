# 06 补充：setState 和页面刷新

对应主文档章节：`6. setState 和页面刷新`

## 它到底做了什么

```dart
setState(() {
  count++;
});
```

这段代码不是单纯“改变量”，而是在告诉 Flutter：

- 状态已经变化
- 当前 Widget 需要重新执行 `build`

## 一个常见误解

不是 `setState` 改了界面，而是 `setState` 触发重新构建，新的状态决定了新的界面。

## 什么时候别乱用

- 页面已经销毁后
- 异步回调回来时组件已不在树里
- `build` 过程中直接触发状态更新

## 入门建议

小页面、小交互优先掌握 `setState`，先建立刷新直觉，再学更复杂的状态管理。

## 一个完整的最小例子

```dart
class CounterPage extends StatefulWidget {
  const CounterPage({super.key});

  @override
  State<CounterPage> createState() => _CounterPageState();
}

class _CounterPageState extends State<CounterPage> {
  int count = 0;

  void increment() {
    setState(() {
      count++;
    });
  }
}
```

这段代码的关键流程是：

1. 用户触发一个动作
2. 你在 `setState` 里改状态
3. Flutter 重新执行 `build`
4. 新的状态显示到界面上

## 一个很重要的习惯

`setState` 里只放“状态修改”本身即可。

比如更推荐：

```dart
setState(() {
  count++;
});
```

而不是把大量无关逻辑都塞进去。
