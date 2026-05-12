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

## 初学者最该避免的问题

- 页面销毁后还 `setState`
- 忘记释放 controller
- 加载、成功、失败三种状态没分开处理
