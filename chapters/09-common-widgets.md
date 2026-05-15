# 09 补充：常用组件

对应主文档章节：`9. 常用组件：Text、Image、Icon、Button、TextField`

## `Text`

最基础的文本组件，先学会：

- `style`
- `maxLines`
- `overflow`

```dart
Text(
  'Hello',
  maxLines: 1,
  overflow: TextOverflow.ellipsis,
)
```

## `Image`

常见来源：

- `Image.asset(...)`
- `Image.network(...)`

初学阶段先知道：

- 本地资源图通常更稳定
- 网络图常要考虑加载失败和占位

## `Icon`

常用于按钮、状态提示、导航栏。

```dart
const Icon(Icons.favorite)
```

## `Button`

先掌握：

- `ElevatedButton`
- `TextButton`
- `OutlinedButton`

一个最小例子：

```dart
ElevatedButton(
  onPressed: () {},
  child: const Text('提交'),
)
```

## `TextField`

最基础的两个点：

- `onChanged`
- `controller`

一个常见写法：

```dart
TextField(
  onChanged: (value) {
    debugPrint(value);
  },
)
```

## 入门建议

先会“显示内容”和“响应交互”，样式细节后面再逐步补。

## 初学者优先级建议

如果你现在只想尽快上手 Flutter 页面，建议先按这个顺序熟悉：

1. `Text`
2. `Button`
3. `TextField`
4. `Image`
5. `Icon`
