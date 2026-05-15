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

```dart
class DetailPage extends StatelessWidget {
  final String title;

  const DetailPage({super.key, required this.title});
}
```

调用时：

```dart
Navigator.push(
  context,
  MaterialPageRoute(
    builder: (context) => const DetailPage(title: '订单详情'),
  ),
);
```

## 什么时候用 `push`，什么时候用 `pop`

- `push`：进入新页面
- `pop`：返回上一页

可以把它理解成：

- `push` 往页面栈里再压一层
- `pop` 把当前这一层弹掉

## 初学者的阅读技巧

看到跳转代码时，先看三件事：

1. 从哪个页面跳出去
2. 要跳到哪个页面
3. 有没有带参数
