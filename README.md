# Niche Compass · 寻道罗盘

**EN** — A cross-platform niche compliance, competitor teardown, and monetization funnel analyzer for AI agents. Give it a "platform + niche" (e.g. `YouTube + personal finance`, `TikTok + cross-border e-commerce`, `Douyin + e-commerce`) and it returns a rules map, peer risk profiles with compliant alternatives, acquisition and monetization paths, funnel ranges, break-even scenarios, a feasibility scorecard, and a 2–4 week validation plan.

**中文** — 面向 AI Agent 的跨平台赛道合规、对标拆解与变现漏斗分析器。输入"平台 + 赛道"（如 `抖音 + 电商`、`YouTube + 财经`、`TikTok + 跨境电商`），输出平台规则地图、同行风险画像与合规替代方案、引流与变现路径、漏斗转化区间、盈亏测算、可行性打分卡和 2–4 周验证方案。

## Two editions / 两个版本

| Folder | Language | Skill name |
|---|---|---|
| `niche-compass/` | English | `niche-compass` |
| `xundao-compass/` | 中文 | `xundao-compass` |

Each folder contains one `SKILL.md`. / 每个文件夹各含一个 `SKILL.md`。

## Install / 安装

- **Agents that support skills**: copy the folder into your agent's skills directory (the folder name must match the `name` in the `SKILL.md` frontmatter).
- **Agents without skill support**: paste the body of `SKILL.md` into the system prompt or custom instructions.
- **支持 Skill 的 Agent**：把文件夹复制到该 Agent 的 skills 目录（文件夹名需与 `SKILL.md` 里的 `name` 一致）。
- **不支持 Skill 的 AI**：把 `SKILL.md` 正文粘贴到系统提示词或自定义指令中。

## How it adapts to your AI / 如何适配不同 AI

The skill detects what the AI can do and runs in one of three tiers. No extra setup is needed.
Skill 会自动判断 AI 的能力并分三档运行，无需额外配置。

| Tier / 档位 | Capability / 能力 | Behavior / 行为 |
|---|---|---|
| 1 | Browser + web | Pauses **once** to confirm logins and niche, then runs end to end / 仅暂停一次确认登录与赛道，之后一路执行 |
| 2 | Web search only | No pause; public-information edition / 不暂停，公开信息版 |
| 3 | No tools | No pause; framework edition, anything unverifiable is marked "could not be completed" / 不暂停，框架版，无法验证的内容标"本次无法完成" |

## Design principles / 设计原则

- No copywriting, and no advice on evading platform review; peer practices are handled as risk profiles with compliant alternatives.
- Every number is a range with a source grade and a confidence level; no reliable data means it says so.
- Every policy carries an official link and retrieval date, or is marked "to be verified".
- 不代写文案、不教规避审核；同行做法只做风险画像并给合规替代。
- 每个数字都是区间，并标注来源级别与置信度；没有可靠数据就明说。
- 每条政策附官方链接与检索日期，查不到标"待核实"。

## Attribution notice / 署名说明

Reports end with **one** attribution line naming the author and contact details. It appears once, at the very end, and is never inserted into the analysis. To turn it off, tell the AI "no attribution", or delete the "Attribution and contact" section (`署名与联系方式` in the Chinese edition) from `SKILL.md`.

报告末尾会附**一行**作者署名与联系方式，整份报告只出现一次，不会插入分析正文。关闭方式：对 AI 说"不要署名"，或删除 `SKILL.md` 中的"署名与联系方式"一节。

## Disclaimer / 免责声明

Outputs are strategy analysis and estimates, not legal, tax, or financial advice. Third-party data is mostly estimated. Platform rules change often; verify on official pages before acting.

输出为策略分析与估算，不构成法律、税务或投资建议。第三方数据多为估算值。平台规则变化频繁，行动前请以官方页面为准。

## Contact / 联系方式

WeChat: ______ · Telegram: ______ · X: ______
