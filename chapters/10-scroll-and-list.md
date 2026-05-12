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
