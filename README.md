# Nomon 改进设计方案

给 Nomon 测试版的一份体验诊断和重构建议，对标 Oura App 的产品结构。

## 一句话

现在的 Nomon 是「你先说，我再帮你」；建议改成「我先让你看见自己的身体，你自然就想说了」。

## 内容

| 文件 | 是什么 |
|---|---|
| [`demo/index.html`](demo/index.html) | **可点击的交互原型**。走一遍完整的「2 分钟自查」流程：身体地图 → 五步问诊 → 结果页。左边解释每一屏在解决什么问题。分数是根据你的输入实时算出来的，不是写死的假数据。 |
| [`docs/design-proposal.html`](docs/design-proposal.html) | 完整设计方案（网页版，含线框对比图） |
| [`docs/design-proposal.md`](docs/design-proposal.md) | 同一份方案的 Markdown 原稿 |

## 在线版（不用 clone，手机上直接点）

- 可点击原型 — https://claude.ai/code/artifact/e9e10945-ccb3-416b-94d4-321ac86f2e19
- 设计方案网页版 — https://claude.ai/code/artifact/adee5f78-548a-4bea-b7f3-6b7118e5b360

## 怎么看

把仓库 clone 下来，直接双击 `demo/index.html` 用浏览器打开就行——纯静态单文件，没有任何依赖，不用装东西、不用起服务器。

```bash
git clone https://github.com/diaanhw/nomon-redesign.git
cd nomon-redesign
open demo/index.html      # macOS
```

## 核心诊断

1. **给予和索取的顺序反了。** Oura 先给价值（戴上就有分数）再要投入；Nomon 现在进门就是空文本框，Insights 还写着 "A pattern shows after a few entries"——把回报推到未知的将来。
2. **把最难的输入方式设成了默认。** 自由文本对用户是开放式作文题。没有传感器不要紧，用结构化自评替代作文：点部位 → 选场景 → 做动作 → 拖滑条。
3. **完全缺「知识」这一层。** Oura 的睡眠分数/生物钟/睡眠负债这些卡，作用是在用户零数据时证明「我懂这件事」。
4. **Myself 页展示的是系统内部状态**（Thoughts 2 / 1 signal），不是用户关心的「我肩膀怎么样、多久好、今天能不能练」。

## 优先级

- **P0** — 身体地图入口 · 2 分钟自查 · 即时结果页 · 12 张知识卡
- **P1** — 恢复分数与贡献因子 · 部位档案与恢复曲线 · 复测提醒
- **P2** — 视频动作分析（建议做成「摄像头当量角器」测活动度，而不是「AI 看视频给诊断」）· 恢复计划日历

## 说明

原型仅为设计演示，不构成医学建议。方案里的「安全底线」一节是硬约束，建议先于功能实现。

---

2026-08-18 ｜ Harvey（问题与方向）+ Claude Code (Opus 5)（方案与原型）
