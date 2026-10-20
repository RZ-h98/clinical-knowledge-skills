---
name: clinical-specialty-knowledge-base
description: 要系统学习某个临床科室（如眼科、心内科、儿科）的教材、国内外指南、职称考试考点、检查图谱，以及每周前沿文献，并建成可核查、可问答调用的中文知识库时使用。
---
# 临床专科知识库构建

目标：为一个临床科室建立分层、带来源、可核查的中文知识库，用于临床问答。面向中国临床医生。学习是助手自己的事，不要出题考用户（除非用户要求）。

## 目录约定
`/workspace/<specialty>-knowledge/`
- `README.md`：教材清单、目录索引（✅/⏳ 状态）、更新日志
- `00-curriculum.md`：按主干教材章节列学习路线、优先级、必会急症清单
- `01-…NN-*.md`：按章节写的教材笔记
- `NN-drug-quickref.md`：药物速查（含国内获批状态）
- `guidelines/`：`INDEX.md`（疾病 × 国内指南 × 国际指南总表）+ 每个疾病组一个文件
- `exams/`：`INDEX.md`、`residency-completion.md`、`attending.md`、`senior.md`、`case-bank.md`
- `imaging/`（或 `diagnostics/`）：该科主要检查各一个文件 + `INDEX.md`
- `literature/`：`INDEX.md`（按周的文献总表）+ `journals.md`（必查期刊清单）+ 每周一个 `YYYY-Www.md`

## 步骤
1. **定教材骨架**：用网页检索确认最新版本（书名、主编、出版社、年份、ISBN、公开目录）：人卫五年制规划教材最新版、八年制版、住培/专科教材，加上 1–3 本国际权威教材或课程。按主干教材的目录拆章节。
2. **教材笔记**（可分 3 轮，每轮 3–5 章）：每个疾病写定义、表现、检查、诊断与鉴别、治疗原则、危险信号。用自己的话归纳，不照抄受版权保护的正文。
3. **指南**：每个疾病组列出国内的中华医学会各分会指南和共识、国家卫健委诊疗指南，以及主要国际学会指南。每条都要有名称、机构、年份或版本、期刊出处和链接。写明关键推荐、随访要求，国内外不一致的地方单独列出来，再把要点并入教材笔记。
4. **考试**：规培结业、主治医师、副高和正高三级，分别整理科目、题型、题量、时长和合格线，各省差异以官方通知为准。辅助刷题平台只用不需要登录就能看到的公开内容，只提炼考点和章节结构，不复制原题、真题或回忆版。按需写自编病例题，并标注「自编练习题」。
5. **检查与影像**：列出该科主要检查和主流图谱书。每类整理正常解剖或正常表现、检查原理与适应证、读片步骤、疾病征象表（疾病｜典型征象｜鉴别要点｜容易误读处），以及伪影和误区。内容来自公开图库、开放获取综述和影像共识。
6. **核实轮**：逐条检索待核项，有原文的对照原文核实。已核实的标 ✓；只核实了名称或是否存在的，标 ✓（名称）；凭已有知识写的标〔知〕；查不到的保留「待核」。
7. **自检**：用 `ls` 和 `wc -l` 检查文件；每个专题文件建议不少于 80–100 行；更新 README 里的状态和日志。
8. **每周前沿文献**（建库后长期做，适合设成每周例行任务）：
   - 先建 `literature/journals.md`，列出两类必查期刊，每周逐刊检索，一本都不能跳：
     - **该专科外文顶刊**：按影响力和亚专科覆盖选 10–20 本（例：眼科为 Ophthalmology、JAMA Ophthalmology、Progress in Retinal and Eye Research、AJO、BJO、Ophthalmology Retina、Ophthalmology Glaucoma、Retina、IOVS、Survey of Ophthalmology、Eye、Acta Ophthalmologica、JCRS、Cornea、Ocular Surface、TVST）。
     - **综合医学及高影响力顶刊里的本专科论文**：NEJM、Lancet、JAMA、BMJ、Annals of Internal Medicine、Nature Medicine、Lancet Digital Health、Lancet Global Health、JAMA Network Open，加上与该科相关的子刊（如 JAMA Pediatrics、Lancet Diabetes & Endocrinology、Diabetes Care），以及 Nature、Science、Cell、Science Translational Medicine、Nature Communications。逐刊用本专科关键词检索（眼科例：eye、ocular、retina、macular、glaucoma、myopia、cataract、uveitis、cornea、visual、ophthalm*），也要算上其他学科研究里涉及本专科的结局，比如药物不良反应、并发症筛查、AI 筛查。
   - 检索方式：期刊官网的 online first 和 current issue，加上 PubMed 按期刊名和日期筛选（过去 7 天）。
   - 其次再查国内核心期刊（中华系列）、主要学会新闻、新指南新共识和药品审批（NMPA/FDA/EMA）。
   - 优先看 RCT、meta 分析、指南或共识、大型队列和监管审批；选 5–10 篇最重要的，顶刊优先。
   - 每篇记录题目、期刊、日期、DOI 或 PMID 链接、研究设计、主要结论（用自己的话写），以及对临床的影响（会不会改变现有做法）。
   - 在 `YYYY-Www.md` 里记下每本必查刊的检索结果，没有相关文章的写「本周无相关」，方便查漏。
   - 写入 `literature/YYYY-Www.md` 并更新 `literature/INDEX.md`；改变实践的结论同步更新到对应的教材笔记或指南文件，并在 README 日志里记一笔。
   - 不编造文献、DOI 或数据；只读到摘要的，标明「仅摘要」。

## 规则
- 不编造书名、指南名称、年份、推荐等级、数值或考试数据。不确定的一律标「待核」。
- 不登录、不绕过付费墙、不批量复制版权内容（教材、图谱、题库）。用户自己提供的 PDF 或截图可以读，读完要用自己的话归纳。
- 药名写通用名，并注明国内获批情况。
- 回答临床问题前先在知识库里检索（`rg`），优先引用标 ✓ 的内容；引用〔知〕或待核内容时，要告诉用户还没核实。

## 并行方式
教材、指南、考试、影像、文献五条线写在不同子目录，可以同时推进，互不改对方的文件。每条线做完一轮后，再按它的待核清单进入下一轮。
