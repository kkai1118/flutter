# 10 补充：列表与滚动

对应主文档章节：`10. 列表与滚动`

## 为什么它这么重要

因为移动端页面里，大量内容都需要滚动展示。

## 最常见的 3 种写法

### `ListView`

适合少量固定 children。

### `ListView.builder`

适合大量或动态列表数据。

### `SingleChildScrollView`

适合“整块内容一起滚动”的场景。

## 一个实战判断

如果是数据列表，优先想 `ListView.builder`；
如果只是一个长页面整体滚动，优先想 `SingleChildScrollView`。

## 一个最常见的列表例子

```dart
ListView.builder(
  itemCount: 20,
  itemBuilder: (context, index) {
    return ListTile(
      title: Text('Item $index'),
    );
  },
)
```

你可以先这样理解：

- `itemCount`：一共有多少项
- `itemBuilder`：每一项怎么长出来

## `ListTile` 为什么常见

因为它能很快搭一个“标题 / 副标题 / 图标 / 点击”的列表项结构。

所以初学做列表页时，用它会很省事。

## 一个高频坑

滚动组件嵌套时，经常会出现高度约束问题。

比如：

- `ListView` 放进 `Column`
- `ListView` 再包 `SingleChildScrollView`

初学阶段先尽量保持：

- 一个主要滚动区域就够了
