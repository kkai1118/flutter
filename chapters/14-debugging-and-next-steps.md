# 14 补充：调试、常见坑与下一步

对应主文档章节：`14. 调试、常见坑与下一步`

## 最实用的 4 个调试习惯

- 先看报错的关键几行，不要只看第一眼红字
- 用 `debugPrint` 输出关键变量
- 用 Flutter Inspector 看 Widget 树和布局
- 先缩小问题范围，再改代码

## 入门阶段最常见的坑

- `Column` 内容溢出
- `Expanded` 不在 `Row` / `Column` / `Flex` 里
- 列表嵌套滚动导致高度异常
- 页面销毁后异步回调还在 `setState`
- `TextField` 的 controller 没有释放

## 下一步建议怎么学

1. 自己写一个列表页 + 详情页 demo
2. 再加一个输入框和按钮交互
3. 再练一次异步加载页面
4. 最后去看真实项目里的 `main.dart`、路由和首页

## 学会的标志

如果你已经能解释这些问题，说明 Flutter 已经入门：

- 为什么 `setState` 后页面会刷新
- 为什么 `Expanded` 不能乱放
- 为什么页面跳转经常依赖 `context`
- 为什么列表优先考虑 `ListView.builder`
