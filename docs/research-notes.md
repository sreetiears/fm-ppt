# 调研笔记：先找参考，再动手

调研日期：2026-10-25。动手前先核对高星项目、经典论文阅读法和去年案例。

## 1. 内容方法：怎么教「看论文」

权威底本是 S. Keshav, *How to Read a Paper*, ACM SIGCOMM CCR, 2007。

核心不是「从第一页读到最后一页」，而是最多三遍：

| 遍次 | 时间 | 目标 | 课后应能回答 |
|------|------|------|--------------|
| 第一遍 | 5–10 分钟 | 鸟瞰，决定要不要继续 | Five C：Category / Context / Correctness / Contributions / Clarity |
| 第二遍 | 约 1 小时 | 抓住主干，不抠证明 | 能把主线加证据讲给别人；图、坐标轴、误差棒要看仔细 |
| 第三遍 | 1–5 小时 | 几乎在脑子里重做一遍 | 能复述结构，指出隐含假设、弱点、可改进处 |

文献调研补充：Scholar 先找 3–5 篇近作 → 各做第一遍并读 Related Work → 找综述 / 共同引用 / 重复作者 → 再看顶会目录。大一不要求做完整综述，但「先扫三五篇再下潜」值得带走。

对新生的改编：

- 第一遍必须现场走完，这是 45 分钟里最该学会的技能。
- 第二遍只示范「先看图和表」，不讲公式推导。
- 第三遍明确说：大一多数时候用不到；只有你准备复现、跟进或给项目提 PR 时才做。

## 2. 去年学长案例：可继承与要改的

材料：`新生研讨课初稿(3).pdf`（发言稿）+ `新生研讨课--开源(3).pptx`。

可继承：

- 口语、停顿、现场提问，而不是念定义。
- 开场两个生活问题，把抽象概念拉回日常。
- 用类比（餐馆 vs 菜谱）再给真实项目。
- 结尾落到社团：贡献不一定写代码。
- 总时长意识：去年是两节各 45 分钟，信息密度偏高。

要改：

- 今年只有 45 分钟，主题换成「如何看论文」。
- 去年 PPT 字太多、蓝色卡片堆叠，投影上难读。今年按 speaker-led：一页一个重点。
- 开源历史、许可证、xz 投毒等不再展开，只在「论文如何帮你进入开源项目」里点一下。

## 3. 主例子：MinerU

主论文：Wang et al., *MinerU: An Open-Source Solution for Precise Document Content Extraction*, arXiv:2409.18839。上海人工智能实验室，项目 https://github.com/opendatalab/MinerU。

适合当教具的原因：

- 开源社团语境：论文和仓库是同一件事的两面。
- 问题具体：PDF 里有公式、表格、双栏，复制出来是乱码。
- 图 1 是四段流水线，第一遍就能画出来。
- 图 3 一眼能看懂「为什么必须先做版面」。
- 表 3 数字对比清楚：论文验证集 mAP 77.6 vs 开源基线 52.8。

第一遍 Five C 预填：

1. **Category**：系统 / 工具论文，多模块文档解析，不是纯理论。
2. **Context**：LLM 和 RAG 需要干净文档数据；现有路线有 OCR、库解析、多模块、端到端多模态。
3. **Correctness**：假设「多模块 + 多样本文档微调 + 规则后处理」能同时保证质量和速度。对新生说：听起来合理，第二遍再用图和表检验。
4. **Contributions**：开源一站式抽取；适应论文 / 教材 / 试卷等多样版面；过滤页眉页脚；跨栏跨页段落；公式表格识别。
5. **Clarity**：结构清楚，图多，适合当第一篇精读样本。

第二遍只带三张「证据」：

- 图 1：预处理 → 解析 → 后处理 → Markdown/JSON。
- 图 3：无版面 OCR 会把双栏读乱。
- 表 3：多样本微调后的版面检测明显好于通用开源模型。

MinerU 2.5（1.2B VLM，粗到细两阶段）只作为「同一项目会写续篇」的彩蛋，避免两篇都讲。

## 4. PPT 制作参考（高星项目）

| 项目 | 约 star | 结论 |
|------|---------|------|
| [hugohe3/ppt-master](https://github.com/hugohe3/ppt-master) | 6.7 万 | 原生 PPTX 流水线完整，作者也写了「不要指望一次成型」。按你的要求只作流程参考，不当主生成器。 |
| [zarazhangrui/frontend-slides](https://github.com/zarazhangrui/frontend-slides) | 3.1 万 | 单文件 HTML、固定 16:9、反 AI slop、先做风格预览。课堂演示主路径。 |
| [alchaincyf/huashu-design](https://github.com/alchaincyf/huashu-design) | 2.6 万 | HTML + 可编辑 PPTX，强调从已有设计上下文长出来。 |
| [chuspeeism/dashi-ppt-skill](https://github.com/chuspeeism/dashi-ppt-skill) | 0.97 万 | 职场主题库大，但偏商务模板。 |
| [presenton/presenton](https://github.com/presenton/presenton) | 1.1 万 | 自托管生成器，对本项目过重。 |
| [icip-cas/PPTAgent](https://github.com/icip-cas/PPTAgent) | 0.5 万 | 学术 agent，EMNLP 2025。 |
| [gitbrent/PptxGenJS](https://github.com/gitbrent/pptxgenjs) / [scanny/python-pptx](https://github.com/scanny/python-pptx) | 0.6 万 / 0.3 万 | 可靠的 PPTX 底层库。教室备用导出用 python-pptx。 |

设计系统：[VoltAgent/awesome-design-md](https://github.com/VoltAgent/awesome-design-md) 的 Claude `DESIGN.md`。

- 画布 `#faf9f5`，珊瑚 `#cc785c`，墨色 `#141413`，深色块 `#181715`
- 标题用衬线（Cormorant Garamond / EB Garamond 替代 Copernicus），正文用人文学 sans（Source Han Sans / IBM Plex Sans 替代 StyreneB）
- 奶油 → 深色 mockup → 偶发整页珊瑚，不要连续两页同一种表面
- 珊瑚只用于强调，不铺满每一页
- 低密度演讲页：一页一个想法，1–3 条要点

## 5. 制作决策

1. 先定 45 分钟讲稿和页大纲，再做视觉。
2. 主交付：可全屏演讲的单文件 HTML（frontend-slides 规则 + Claude 视觉）。
3. 教室备份：同内容精简 PPTX（python-pptx）。
4. 风格已由你指定为 Claude 系，不再做三套风格海选，避免耽误撰稿。
5. 图优先用论文原图和 CSS 图解，少用装饰插画。
