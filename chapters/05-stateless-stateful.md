# 05 补充：StatelessWidget 和 StatefulWidget

对应主文档章节：`5. StatelessWidget 和 StatefulWidget`

## 一句话区分

- `StatelessWidget`：界面由外部输入决定，自己不改状态
- `StatefulWidget`：界面会随着内部状态变化而变化

## `StatelessWidget` 常见场景

- 标题组件
- 卡片组件
- 固定展示块

## `StatefulWidget` 常见场景

- 计数器
- 输入框页
- Tab 切换页
- 加载状态页

## 判断方法

如果组件里没有“点一下就变、加载后会变、输入后会变”的需求，优先考虑 `StatelessWidget`。

## 一个最直观的判断题

### 适合 `StatelessWidget`

- 固定标题
- 固定介绍卡片
- 只负责展示父组件传进来的内容

### 适合 `StatefulWidget`

- 计数器数字会变化
- 输入框内容要跟踪
- 加载中 / 成功 / 失败界面会切换

## 不要把“有参数”误认为“有状态”

比如：

```dart
class UserCard extends StatelessWidget {
  final String name;

  const UserCard({super.key, required this.name});
}
```

它虽然有 `name` 参数，但仍然可以是 `StatelessWidget`。

关键不是“有没有参数”，而是：

- 这个组件自己要不要维护变化中的状态
