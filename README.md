<div align="center">

# Arena · 电竞赛事看板与虚拟积分预测社区

**把「我觉得这队能赢」变成一条可以被记分的预测。**

`个人自建 · 纯业余爱好` · `虚拟积分` · `无充值 · 无提现 · 无兑换` · `邀请制 · 朋友之间娱乐`

[English](#english) · [常见问题](docs/FAQ.md) · [声明](DISCLAIMER.md)

</div>

> [!IMPORTANT]
> **站内积分完全虚拟，由系统免费发放。**
> 不能购买、不能转让、不能提现、不能兑换任何现实中的财物或权益，站点也没有任何支付通道。
> 积分唯一的用途是给预测记分、排名次。这是一个电竞爱好者的数据看板与预测游戏，
> 面向成年爱好者的小范围娱乐，与任何形式的现实财物交易无关。
>
> **一个人业余搭的站，随时可能出错、变更或关停，不作任何承诺。** 当个乐子就好。

---

## 这是什么

一个人业余搭的电竞赛事站点，做两件事：

1. **把赛事数据整理清楚** —— 赛程、比分、积分榜、晋级路线、逐局阵容与选手数据，一页看完；
2. **让预测能被记分** —— 用虚拟积分对赛果做预测，结算后进排行榜，比的是眼光，不是手速也不是积分多。

目前覆盖 **英雄联盟**（LPL 各赛段、MSI、全球总决赛）与 **王者荣耀**（KPL、挑战者杯、KWC）两个项目。
顶栏一键切换，赛事按项目分区。

纯个人爱好，不商业化、不接广告、不收钱，也就没有客服、没有服务承诺 —— 有空就修，忙起来可能放几天。
这一点先讲清楚，免得期待落空。

---

## 加入我们

站点地址：**https://arena.zswclub.com**

注册需要邀请码 —— 不是门槛，是为了让规模长在能聊得起来的范围里。两种拿码方式：

- 在本仓库 [提一个 Issue](../../issues/new?template=invite-request.yml) 申请（推荐，有表单模板，处理完会关掉）
- 或到 [Discussions](../../discussions) 打个招呼，顺便聊赛事

注册只要用户名、昵称、密码，**不收手机号、不收邮箱、不接入任何第三方登录**。

---

## 几个别处不太有的地方

### 出线情景推演：不给概率，给确定结论

小组赛打到一半，最想知道的其实不是「出线率 63%」，而是「我还有没有戏」。

站点会把小组剩余赛程的**全部**可能结果穷举一遍，然后回答三个确定的问题：

- 谁已经锁定出线、谁已经数学淘汰；
- 剩下哪一场比赛会决定谁的命运；
- 那一场是「只看谁赢」，还是「零封还是打满也会改结果」。

页面主体是一条出线线和每支队的名次跨度条：整根在线内 = 稳了，整根在线外 = 没了，
横跨这条线 = 命运未定。点队名切到该队视角，会分开列出「自己要打的」和「只能指望别人的」。

概率和确定性是两回事：概率那边说 63%，这边说「一定」。剩余场次太多算不出确定结论时，页面会照实说还差几场，不编。

### 报价来自模型，而不是拍脑袋

1. 两队的 **Elo 评级**（按局计算、同项目内跨赛事共用一个池）先算出单局胜率；
2. 胜率展开成 BO3 / BO5 的**完整比分分布**，这就是开盘报价；
3. 之后每一笔预测都按 **LMSR 成本函数**推动报价 —— 越早看准，记分越好。

因为跨赛事共用评级池，全球总决赛时 LPL 队伍可以直接和 LCK / LEC 比较；而两个游戏的队永远不会互相比。

### 一场比赛只有一个市场，四类题目永远自洽

胜负、正确比分、让分、总局数，是**同一个比分分布的四种切法**：

| 题目 | BO3 下的含义 |
|---|---|
| 胜负 | 主胜 = {2:0, 2:1} |
| 正确比分 | 单点，记分系数最高 |
| 让分 ±1.5 局 | 主队 −1.5 = 净胜两局 = {2:0} |
| 总局数 2.5 | 大 = 打满三局 = {2:1, 1:2} |

所以选「正确比分 2:0」也会推动「胜负」的报价，四组题目互相一致，**不存在无风险套利的缝**。

### 排行榜比的是眼光，刷不出来

排名按**题目**计，不按笔数计：一个题目只算一次（同一题目投几笔也算一次，而且要这个题目**净赚**才算赢），
一注组合预测也算一次（全中即为赢）。

所以「反复追投」刷不出成绩，「两边都选，总有一笔中」也刷不出来 —— 对冲一定会赔掉回收的那部分积分。
收益率榜与命中率榜另设双门槛（至少 10 个题目、累计投入 5,000 积分），
免得「10 个题目各投 10 分」和「投 100 赚 300」这种极小样本霸榜。

### 数据不靠上游活着

赛程比分走公开的电竞数据源实时更新，各游戏官方赛事网每日补位（官方分组、赛季名单、逐局细节）。
关键是**抓到的东西都在本地存一份，页面只看自己这份**：

| 层 | 上游哪天下线之后 |
|---|---|
| 赛程、比分、积分榜、战队 | 照常显示与回看 |
| 逐局首发与选手数据 | 照常显示 |
| 队徽、头像、英雄与装备图 | 都存了本地一份，照常显示 |

历史赛事随时回看，上游停更时页头会标出最后更新时间。

### 逐局看到底

比赛详情页可以逐局查看双方首发：位置、英雄、KDA、经济、出装与符文，以及单局 MVP。
官方站升级过的对局还有逐位置对位详情 —— 伤害三段拆分、承伤与经济占比、视野得分、15 分钟经济差。

---

## 玩法一览

| | |
|---|---|
| **单场预测** | 胜负 / 正确比分 / 让分 / 总局数，同一个比分分布派生 |
| **组合预测** | 2–5 项连乘，全中才算成。报价提交瞬间锁定 |
| **长周期预测** | 赛段冠军、各组小组第一。概率来自剩余赛程的 2 万次蒙特卡洛模拟，每场结算后重算，所以报价会自己移动 |
| **提前离场** | 停止接受预测之前，随时可以卖出持仓，锁定盈亏 |
| **积分来源** | 初始 10,000；每日签到 500 起、连签递增封顶 2,000；低余额补给；成就奖励 |
| **积分回收** | 每笔预测按比例回收少量积分（单项 2% / 组合 5% / 长周期 3%），用于抑制积分通胀 |

规则口径都摆在明面上：单场单人上限、组合预测最大记分、开赛前 5 分钟停止接受预测
（比赛被提前推成「进行中」时也立刻停）。页面上写的额度就是实际执行的额度，不存在两套说法。

---

## 声明

- 站内积分为虚拟计分工具，**免费发放、不可购买、不可转让、不可提现、不可兑换任何现实财物或权益**；站点不设任何支付、充值、打赏或结算通道。
- 本站为电竞爱好者个人业余搭建的数据展示与预测记分工具，**不提供任何形式的资金交易服务**，与任何现实财物博弈无关。
- **不作任何承诺**：一个人业余维护，可用性、数据准确性、功能延续性与反馈处理时间均不作保证，站点可能随时变更、中断或关停。
- 赛事数据来自公开的数据源与公开页面，仅作非商业性的爱好者展示与研究之用。相关赛事名称、队伍名称、图片与商标归各自权利人所有，本站与其没有任何隶属或合作关系。权利人如有异议，请通过 Issue 联系，我会立即移除相应内容。
- 完整版本见 [DISCLAIMER.md](DISCLAIMER.md)。

---

<a name="english"></a>

## English

**Arena** is a hobby-built esports dashboard with a **play-money** prediction layer,
run by one person for a small circle of fans. It currently covers *League of Legends*
(LPL / MSI / Worlds) and *Honor of Kings* (KPL / KWC).

> **All points are virtual and free.** They cannot be purchased, transferred, withdrawn,
> or exchanged for anything of real-world value, and the site has no payment channel of any
> kind. Points exist only to score predictions and rank participants. This is a hobby
> project for entertainment, not a financial service.
>
> **No guarantees of any kind** — availability, data accuracy, continuity of features, and
> response times are all unpromised. It is a spare-time project and may change, break, or
> shut down at any moment.

What makes it interesting:

- **Qualification scenarios, not just probabilities.** It enumerates *every* remaining outcome of a
  group stage and answers with certainty: who is already through, who is mathematically out,
  which single match decides whose fate, and whether the *margin* of that match matters.
- **Model-driven quotes.** Elo ratings (per-game, shared across tournaments within a title)
  produce a per-map win probability, expanded into a full scoreline distribution, then priced
  continuously by an **LMSR** market maker.
- **One market per match.** Match winner, exact scoreline, map spread and total maps are four
  slices of the same distribution — always mutually consistent, no risk-free arbitrage.
- **Skill-based leaderboards.** Ranked per *question*, not per entry, with minimum volume and
  total-points thresholds — so repeated entries and hedging cannot inflate a record.
- **Data that outlives its sources.** Scores, per-map rosters and images are all kept locally,
  so pages keep working and past tournaments stay browsable even after an upstream source
  disappears.

Site: **https://arena.zswclub.com** · Registration is invite-only;
[open an issue](../../issues/new?template=invite-request.yml) to request one.
