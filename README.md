# Gemini 4 Neon震撼上线！编程Agent夺冠，暴击Opus 5.5

标题：Gemini 4 Neon 震撼上线！编程 Agent 夺冠，暴击 Opus 5.5

正文：

2026 年 11 月 18 日，Google DeepMind 发布 Gemini 4 Neon。官方博客 [Introducing Gemini 4 Neon](https://blog.google/innovation-and-ai/models-and-research/gemini-models/introducing-gemini-4-neon/) 由 Koray Kavukcuoglu 执笔，对这款模型的定位说得很明白：**把前沿级智能，与「把一项复杂任务从头到尾做完」的速度放在一起**，面向软件工程、知识工作与科学研究。

官方给出的可用入口包括：Gemini API（Google AI Studio）、Gemini for business、面向付费 Google AI Pro / Ultra 用户的 Google Antigravity，以及 Gemini 应用中的 Pro、Ultra 订阅。如果你在国内更想走现成的网页对话入口，也可以先打开第三方门户 [https://gemini-ultra.top/list/#/home](https://gemini-ultra.top/list/#/home)。该站点的界面品牌是 **momoAI.New**，并非 Google 或 Gemini 的官方网站。下文按当前截图说明：怎么进入 GeminiPro 节点，再在模型菜单里勾选 4 Neon。

## 先看跑分：19 项里领先 16 项，有 3 项没拿下

标题里的「暴击 Opus 5.5」，说的是 Google 公开的那张对比表。对手是 Claude Opus 5.5 与 GPT-6.2 Sol，并非与所有模型逐一比较，表中未出现的型号也没有写进来。评测方法说明见 [Gemini 4 Neon evals methodology](https://deepmind.google/models/evals-methodology/gemini-4-neon)。

下面按 Google 公开对比表整理，数字保持原样。

| 评测 | Gemini 4 Neon | Claude Opus 5.5 | GPT-6.2 Sol |
| --- | --- | --- | --- |
| AA Index v5.0.1 | 61 | 59 | 57 |
| Vals Index v2.2 | 70.9% | 70.1% | 66.1% |
| CursorBench 4.1 | 65.4% | 58.1% | — |
| Terminal-bench 4.1（cheating-adjusted） | 65.2% | 65.8% | 61.5% |
| FrontierCode 2.0 main | 46.2% | 47.3% | 43.8% |
| SWE-sweep provider harness | 39.0% | 10.1% | 8.3% |
| SWE-sweep Mini-SWE harness | 12.8% | 3.6% | 11.6% |
| AutomationBench | 56.3% | 42.5% | 41.3% |
| Agents' Last Exam v1.1 | 75.8% | 71.6% | 73.0% |
| RiemannBench | 84.0% | 80.0% | 80.0% |
| Terminal-Bench-Science 0.1 | 70.5% | 63.3% | 68.0% |
| HLE-Diamond | 71.3% | 67.9% | 64.0% |
| MKA Climb WSR | 56.5% | 53.0% | 52.7% |
| Chartography | 73.5% | 66.3% | 75.1% |
| LVBench | 89.0% | 83.7% | 87.6% |
| GraphWalks 256k to 1M BFS F1 | 95.2% | 66.8% | 80.1% |
| CWE-Bench v2 | 70.7% | 67.1% | 66.0% |
| SEC-bench Pro | 90.5% | — | 88.3% |
| WebExploitBench v1.2 | 51.3% | 37.1% | — |

按表中 19 行逐项数下来，Gemini 4 Neon 领先 **16 项**。没拿下的 3 项，需要单独说清楚：

- Terminal-bench 4.1（cheating-adjusted）：Claude Opus 5.5 拿到 65.8%，略高于 Neon 的 65.2%；GPT-6.2 Sol 为 61.5%
- FrontierCode 2.0 main：Claude Opus 5.5 为 47.3%，也略高于 Neon 的 46.2%；GPT-6.2 Sol 为 43.8%
- Chartography：GPT-6.2 Sol 为 75.1%，高于 Neon 的 73.5%；Claude Opus 5.5 为 66.3%

其余项目里差距比较明显的几项是：CursorBench 4.1 为 65.4% / 58.1% / —，SWE-sweep provider harness 为 39.0% / 10.1% / 8.3%，AutomationBench 为 56.3% / 42.5% / 41.3%，GraphWalks 256k to 1M BFS F1 为 95.2% / 66.8% / 80.1%。完整数字以原表为准，这里不作改写。

另外两项官方成绩也值得单独记一笔，因为它们撑起了标题里的「编程 Agent 夺冠」：

- Artificial Analysis Coding Agent Index：Gemini 4 Neon 以 **58.6** 分排在第 1 位。来源是 Google Antigravity 博客 [Gemini 4 Neon in Google Antigravity](https://antigravity.google/blog/gemini-4-neon-in-google-antigravity/)
- Artificial Analysis Intelligence Index：在 xhigh thinking 下拿到 **61** 分，总榜第 3。对比表第一行的 AA Index v5.0.1 也是 61 / 59 / 57，与这条官方成绩对得上

在 Google Antigravity 里，Neon 还能充当 Orchestrator，调度并行的 Hydrogen 子代理共同完成任务。按官方分层，Carbon 对应最难、跨度更长的工作，Hydrogen 偏向日常快速协助，Neon 则在深度与效率之间取平衡。

## 三则官方演示：从图灵书房到雪场

官方博客里给出了几段演示，用来看 Neon 在复杂长任务上的完成方式，并不是我们本地复现的结果。

### 1. 用 /swarm 搭出图灵的书房

第一段是在 Google Antigravity 里使用 `/swarm`，按 1936 年剑桥国王学院的场景，重建艾伦·图灵的书房，并做成可交互的 3D 空间。动画里既能从窗外望进书房，也能看到书架和书桌。

![官方演示：在 Google Antigravity 中用 /swarm 重建艾伦·图灵 1936 年剑桥国王学院书房的交互式 3D 场景](https://upload.maynor1024.live/file/1795052274850_05-turing-study.gif)

### 2. 十万格表格、五十多万条公式，做成视觉实验室

第二段演示的标题是「Neon — CV Lab 100K」：一张 Google 表格里有 **100,000 个单元格**、超过 **500,000 条实时表格公式**，没有内嵌图片，也没有使用 Apps Script。界面里能看到 Color Canny、3D Depth Map、3D Relighting 等模式。换句话说，这些视觉效果全是表格公式现场算出来的。

![官方演示：名为 Neon — CV Lab 100K 的 Google 表格，用十万单元格和五十多万条实时公式完成颜色边缘、深度图和重新打光等视觉效果](https://upload.maynor1024.live/file/1795052281160_06-spreadsheet-cv-lab.gif)

### 3. 从零写一个勃朗峰滑雪模拟器

第三段是第一人称 WebGL2 自由滑雪模拟器，地形用的是勃朗峰和霞慕尼的真实高程。官方说明是：10,200 行自定义着色器，120 Hz 物理，六条高山线路，动态雪轨、板块雪崩和空间音频，并且没有使用现成素材包。

![官方演示：基于勃朗峰和霞慕尼真实高程、从零写就的第一人称 WebGL2 自由滑雪模拟器](https://upload.maynor1024.live/file/1795052282368_07-ski-simulator.gif)

## 官方定价，以及能在哪用

以下价格是 **Google 官方 API** 的报价，单位是美元 / 100 万 tokens，别和第三方门户的套餐混为一谈：

- 输入：$3
- 缓存输入：$0.15（相对输入价优惠 95%）
- 输出：$15
- 上下文长度：100 万 tokens

官方还给出了任务成本的对比口径：在默认的 high thinking 下，单任务成本大约比 Carbon 低 **32%**；在 Vals / Agent Arena、同样走 high thinking 时，单任务成本大约比当时领先的竞品前沿模型低 **50%–80%**。

可用入口再汇总一次：Gemini API（Google AI Studio）、Gemini for business，付费 Google AI Pro / Ultra 用户可在 Google Antigravity 中使用，Gemini 应用则面向 Pro 和 Ultra 订阅用户。

## 国内第三方入口：打开 GeminiPro 节点，再选 4 Neon

如果你主要是在国内打开网页直接用，可以走这个第三方门户：

[https://gemini-ultra.top/list/#/home](https://gemini-ultra.top/list/#/home)

再说明一次：这是第三方平台，界面品牌是 **momoAI.New**，不是 Google 或 Gemini 的官方站点。侧栏还能看到 GPTPlus、SuperGrok、AI 绘图、ClaudeProMax、GPTimage2 独立站、GPT 代充值站、Codex 国内站、永久导航站、在线商店和卡密兑换。页脚标注为 © 2026 momoAI.New 20261109233823。本文没有商店或套餐截图，因此不写具体售价；如果要购买或兑换，请进入站内「在线商店」或「卡密兑换」，以当天页面显示为准。

进入后，左侧点击「GeminiPro节点」。本次截图里，全部 **23** 个节点，推荐 **9** 个、繁忙 **14** 个，右上角官网状态显示「正常运行」。挑选方式和这类门户一贯的用法相同：优先看「推荐」，再看负载更低、绿色条更短的节点，点进去即可。

![第三方门户 momoAI.New 的 GeminiPro 节点列表：全部 23 个，推荐 9 个，繁忙 14 个，官网状态为正常运行](https://upload.maynor1024.live/file/1795052271208_02-gemini-ultra-nodes.png)

进到对话界面后，首页提示是 “Where should we start?”。点开模型下拉菜单，当前可见这些选项：

- Auto：Adapts to your needs
- Everyday help：4 Hydrogen
- Deeper analysis：4 Neon（本次已勾选）
- Code & complex work：4 Carbon（带锁图标；截图里能看到锁，这里不猜测它代表什么）
- Thinking level

要把对话切到 Neon，选中「Deeper analysis / 4 Neon」即可。

![Gemini 对话页模型菜单：首页提示为 Where should we start?，当前勾选 Deeper analysis 下的 4 Neon，同时可见 4 Hydrogen、带锁图标的 4 Carbon 和 Thinking level](https://upload.maynor1024.live/file/1795052265878_01-gemini-neon-menu.png)

官方模型今天已经放出，国内这条第三方入口的模型菜单里也已经能看到 4 Neon。先从推荐、负载较低的 GeminiPro 节点进去，再勾上 Neon，就可以开始试用。入口再放一次：

[https://gemini-ultra.top/list/#/home](https://gemini-ultra.top/list/#/home)
![image.png](https://files.maynor1024.live/uploads/user/5c36eb37-a8d1-4c2e-8703-a9f7894ffd8f/d1c2be77-4cc2-468c-bda0-46d6fc004a21.png)
