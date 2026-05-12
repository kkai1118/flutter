# 11 补充：页面跳转与路由

对应主文档章节：`11. 页面跳转与路由`

## 入门先掌握两个动作

### 进入下一页

```dart
Navigator.push(
  context,
  MaterialPageRoute(
    builder: (context) => const DetailPage(),
  ),
);
```

### 返回上一页

```dart
Navigator.pop(context);
```

## 为什么很多跳转代码都依赖 `context`

因为 Navigator 通常也是从当前 Widget 树的上下文里找到的。

## 参数怎么传

入门阶段优先用构造函数传参，这样最直观、最容易看懂。
