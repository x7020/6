# 抖音极速版商品遍历 v3（SKU + 专享价）

适配：iOS 16.6、抖音极速版 39.5.0、TrollFools 裸 dylib 注入。

## 每个商品的动作

1. 进入商品详情。
2. 动态识别并点击 `共N款`（数量不限）。
3. 等待 SKU 弹层 `IESECPdpSKUViewController`。
4. 点击弹层右上角 X 关闭。
5. 点击详情页底部左侧 `专享价 / 抖音商城App专享`。
6. 等待后返回商品列表，继续下一个。
7. 翻页慢时持续等待；识别 `商品已全部展示` 后停止。

没有“共N款”的商品会跳过 SKU 步骤，直接点击专享价。没有专享价时也会继续返回，不会卡死。

## 悬浮按钮

- 单击：开始 / 暂停 / 继续
- 双击：修改延迟和随机抖动
- 长按：停止并重置
- 拖动：移动按钮

## 推荐延迟

- 详情动作前：2.0 秒
- SKU 弹层：1.2 秒
- 专享价后：1.0 秒
- 翻页基础：5.0 秒（慢网）
- 翻页最长：25 秒
- 返回列表后：1.0 秒
- 随机抖动：1.0～1.5 秒

## 编译

覆盖 GitHub 仓库根目录的：

```text
ProductLooper.m
.github/workflows/build.yml
README.md
```

进入 Actions，运行 `Build DouyinLite ProductLooper v3 Universal dylib`，下载 `DouyinLiteProductLooper-v3-Universal`。

注入前移除 `ProductProbe.dylib` 和旧版 ProductLooper，只保留新生成的 `DouyinLiteProductLooper.dylib`。
