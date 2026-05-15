# 12 补充：生命周期与异步界面

对应主文档章节：`12. 生命周期与异步界面`

## 生命周期先记两个

- `initState`：初始化后执行一次
- `dispose`：销毁前执行一次

## 最常见用途

```dart
@override
void initState() {
  super.initState();
  loadData();
}
```

```dart
@override
void dispose() {
  controller.dispose();
  super.dispose();
}
```

## `FutureBuilder` 适合什么场景

适合“界面依赖一个异步结果”时使用，比如：

- 页面首次请求数据
- 本地配置读取
- 延迟初始化内容

一个最小例子：

```dart
FutureBuilder<String>(
  future: fetchName(),
  builder: (context, snapshot) {
    if (!snapshot.hasData) {
      return const CircularProgressIndicator();
    }
    return Text(snapshot.data!);
  },
)
```

看这段代码时，先抓三件事：

- 等的是什么 `future`
- 加载中显示什么
- 有结果后显示什么

## 初学者最该避免的问题

- 页面销毁后还 `setState`
- 忘记释放 controller
- 加载、成功、失败三种状态没分开处理

## 一个很常见的页面流程

Flutter 页面里，你经常会写出这样的节奏：

1. `initState` 里触发初始化
2. 异步去拿数据
3. 数据回来后刷新界面
4. 页面销毁时释放资源

只要先把这条主线看懂，很多页面代码都会变得更容易读。
