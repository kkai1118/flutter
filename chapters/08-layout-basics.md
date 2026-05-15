# 08 补充：基础布局

对应主文档章节：`8. 基础布局：Row、Column、Expanded、Container`

## 先掌握这 4 个

- `Row`：横向布局
- `Column`：纵向布局
- `Expanded`：在 Flex 布局中占满剩余空间
- `Container`：尺寸和装饰容器

## 两个高频概念

### 主轴和交叉轴

- `Row` 的主轴是横向
- `Column` 的主轴是纵向

### 约束

Flutter 布局不是“想多大就多大”，而是父组件先给约束，子组件再在约束里布局。

## 为什么初学者总卡布局

因为很多问题表面看像组件属性不对，本质上其实是：

- 父组件给的空间不够
- `Expanded` 放错位置
- 嵌套滚动导致高度约束异常

## 一个最常见的布局例子

```dart
Row(
  children: [
    const Icon(Icons.home),
    const SizedBox(width: 8),
    Expanded(
      child: Container(
        color: Colors.blue,
        height: 40,
      ),
    ),
  ],
)
```

这段代码里：

- `Row` 负责横向摆放
- `Expanded` 负责吃掉剩余宽度
- `Container` 负责真正显示区域

## `Expanded` 最容易记错的点

它通常要放在：

- `Row`
- `Column`
- `Flex`

这类 Flex 布局里。

如果放错位置，往往就会直接报布局错误。

## 初学者读布局的建议顺序

1. 先看最外层是 `Row` 还是 `Column`
2. 再看有没有 `Expanded` / `Flexible`
3. 最后再看 `Container`、`Padding`、`Center` 这些装饰和定位组件
