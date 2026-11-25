# Scientific Agent Skills：177 个科研 skill，把 AI 变成你的科研助手

> 生物、化学、医学、物理、工程、数据分析、科研写作……一套开源 skill 装进 Claude Code 或 Codex，查数据库、跑分析、写论文都有现成的做法。

**项目地址：** https://github.com/K-Dense-AI/scientific-agent-skills

**本教程 GitHub 版：** https://github.com/hubollsoldre/scientific-skills-guide-cn

---

## 一、它是什么

Scientific Agent Skills 是 K-Dense 团队开源的科研 skill 合集（MIT 协议），GitHub 上约 5.8 万 Star，项目还发表了配套论文（arXiv:2609.00065）。以前叫 Claude Scientific Skills，现在改名后支持更多 AI 工具。

**它解决的问题：** AI 本身会写 Python，但科研里的专业工具（比如 RDKit、Scanpy、PubMed、UniProt）各有各的用法和坑。这套 skill 把每个工具的正确用法、科研规范、检查步骤都写好了，AI 照着做，结果更靠谱，也不用你自己翻文档。

**一共有多少：**

- **177 个 skill**，覆盖 20 多个学科方向
- **100 多个科研数据库**的查询方法：PubChem、ChEMBL、UniProt、PDB、AlphaFold、KEGG、ClinicalTrials.gov 等
- **70 多个常用科研 Python 包**的用法：RDKit、Scanpy、scikit-learn、PyTorch Lightning、BioPython、Qiskit 等
- **30 多个分析和写作工具**：文献综述、论文写作、同行评审、做海报和幻灯片、画示意图

**支持的工具：** Claude Code、Codex、Cursor、Gemini CLI、Google Antigravity 等。

**适合谁：** 生物、化学、医学、材料、物理等方向的研究生和科研人员，以及需要做数据分析、写论文的人。

---

## 二、它能帮你做什么

### 按学科分

| 方向 | 能做的事（举例） |
| --- | --- |
| 生物信息与基因组 | 序列分析、单细胞 RNA-seq、CRISPR 筛选、引物设计、变异注释、系统发育 |
| 化学信息与药物发现 | 分子性质预测、虚拟筛选、ADMET 分析、分子对接、先导化合物优化 |
| 临床研究 | 临床试验数据、药物基因组学、药代动力学建模 |
| 显微与医学影像 | 荧光显微定量、DICOM 处理、数字病理 |
| 神经科学 | BIDS 数据集、电生理记录、生理信号分析 |
| 机器学习 | 深度学习、强化学习、时间序列、模型可解释性、贝叶斯方法 |
| 材料、化学与物理 | 晶体结构分析、计算化学、天文数据、量子计算 |
| 工程与仿真 | 电池模型、化学动力学、流体力学、过程优化 |
| 数据分析与可视化 | 统计分析、网络分析、论文级图表、大规模数据处理 |
| 实验室自动化 | 移液方案、仪器控制、实验流程自动化 |

### 不分学科、人人能用的

| skill 名字 | 做什么 |
| --- | --- |
| `literature-review` | 文献综述 |
| `paper-lookup` | 在 PubMed、arXiv、bioRxiv、Semantic Scholar 等 10 个学术库里查论文 |
| `scientific-writing` | 科研写作，每个说法都能追溯到证据 |
| `peer-review` | 模拟同行评审，给论文挑刺 |
| `scientific-brainstorming` / `hypothesis-generation` | 头脑风暴、提出研究假设 |
| `scientific-critical-thinking` | 批判性分析一个研究 |
| `research-grants` | 写基金申请 |
| `statistical-analysis` | 统计分析 |
| `scientific-visualization` | 画论文级图表 |
| `scientific-slides` / `latex-posters` / `pptx-posters` | 做学术幻灯片和海报 |
| `scientific-schematics` / `infographics` | 画示意图、信息图 |
| `citation-management` | 管理参考文献 |

---

## 三、怎么装

这套 skill 装在 **Claude Code** 或 **Codex** 里用，两个有一个就行。先看你属于哪种情况：

### 情况 A：已经有 Claude Code 或 Codex

**第 1 步：准备两个小工具**

- **Node.js 22.20 以上**：安装命令要用到。终端里输入 `node -v` 能看到版本号就说明有了
- **uv**：很多 skill 要用它装 Python 依赖

装 uv（Mac / Linux）：

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

Windows 在 PowerShell 里运行：

```powershell
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

装完输入 `uv --version` 能看到版本号就行。

**第 2 步：装 skill（推荐只装需要的）**

项目作者自己也建议：**不要一次全装**，用到哪个装哪个。

只装一个，比如文献综述，装到 Claude Code：

```bash
npx skills add K-Dense-AI/scientific-agent-skills --skill literature-review -a claude-code
```

装到 Codex，把结尾换成 `-a codex`：

```bash
npx skills add K-Dense-AI/scientific-agent-skills --skill literature-review -a codex
```

想自己挑：不带 `--skill`，运行后会列出全部 skill 让你勾选：

```bash
npx skills add K-Dense-AI/scientific-agent-skills
```

默认装在当前项目里，想所有项目都能用，加上 `-g`。

**第 3 步：确认装好**

```bash
npx skills list
```

能看到刚装的 skill 名字就对了。

### 情况 B：Claude Code 和 Codex 都还没有

推荐用 **V2Code**：**一个 Key 同时能用 Claude Code 和 Codex**。

1. 打开 **v2code.ai**，注册并创建一个 API Key
2. 按网站「使用教程」里的步骤装好 Claude Code 或 Codex（Mac、Windows 都有图文步骤，大约 10 分钟）
3. 能正常对话后，回到上面的 **情况 A**

📖 教程入口：https://www.v2code.ai/docs/quick-start

---

## 四、怎么用

装好后直接用中文说要做什么就行，AI 会自己挑合适的 skill。**小技巧：开头加一句"尽量使用你可用的 skill"**，它会更积极地调用。

**例 1：文献综述**

```
尽量使用你可用的 skill。帮我做一份"单细胞测序在肿瘤免疫中的应用"的文献综述，查近三年的论文，按研究方向分类总结，列出每篇的链接。
```

**例 2：单细胞数据分析**

```
尽量使用你可用的 skill。用 Scanpy 读取我这份 10X 数据，做质控和去双细胞，鉴定细胞类型，做差异表达分析，再画图并写一份分析报告。
```

**例 3：药物发现**

```
尽量使用你可用的 skill。从 ChEMBL 查 EGFR 抑制剂（IC50 < 50nM），用 RDKit 分析构效关系，在 PubMed 上查耐药机制，再出可视化图表和一份总结报告。
```

**例 4：给自己的论文挑刺**

```
用 peer-review skill，按顶会审稿人的标准审一下 paper/ 里的这篇论文，列出主要问题和修改建议。
```

**也可以直接点名：** 在提示里写出 skill 的名字（比如 `scientific-writing`），它就会用这个 skill。

---

## 五、安全提醒

skill 能让 AI 执行代码、装软件包、联网、改文件，装之前要心里有数：

- **只装你需要的。** 现在仓库里有不少社区贡献的 skill，作者团队也说没法把每一个都审得很细
- **装之前看一眼 `SKILL.md`。** 每个 skill 都写了它做什么、用哪些包、连哪些外部服务，看着不对就别装
- **优先用 K-Dense 团队自己写的 skill**，这些经过了他们内部审查
- 项目每周会做一次安全扫描，结果公开在仓库的 `docs/security-report.md`

---

## 六、使用提醒

- **结果要自己核对。** skill 提供的是经过整理的起点，结论要在你自己的数据和环境里验证
- **临床相关的 skill 只用于研究。** 项目明确说明，这些 skill 不能用来给具体病人做诊断或治疗决定
- **每个科研方向用单独的 Python 环境。** 不同 skill 依赖的包版本可能冲突，分开装省很多麻烦
- **装 skill 不等于装好了依赖。** 初次用某个 skill 时，AI 会按它的说明装需要的 Python 包

---

## 七、链接汇总

- 项目地址：https://github.com/K-Dense-AI/scientific-agent-skills
- 本教程 GitHub 版：https://github.com/hubollsoldre/scientific-skills-guide-cn
- Claude Code / Codex 安装教程（V2Code）：https://www.v2code.ai/docs/quick-start
