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
