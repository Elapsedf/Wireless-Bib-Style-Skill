# Wireless Bib Style

## Description

Wireless Bib Style is a Codex skill for auditing and lightly normalizing BibTeX files against a wireless-communications IEEE bibliography template. It helps keep author names, IEEE journal abbreviations, conference `Proc.` formatting, month/address fields, arXiv entries, and duplicate keys consistent across LaTeX papers.

## Introduction

The repository contains:

- `SKILL.md`: the Codex skill instructions.
- `template.bib`: the canonical IEEE BibTeX string/template file.
- `references/style-rules.md`: the audit checklist and preferred entry shapes.
- `agents/openai.yaml`: a small UI prompt definition for Codex.

The skill is intentionally local-style oriented. It does not treat every BibTeX variant as wrong; it compares a paper's bibliography against the template and reports clear mismatches separately from judgment calls.

## Installation

Clone the repository directly into your Codex skills directory:

```bash
mkdir -p ~/.codex/skills
git clone https://github.com/Elapsedf/Wireless-Bib-Style.git ~/.codex/skills/ieee-bib-style-audit
```

If you already cloned it elsewhere, copy the repository into the skill directory:

```bash
mkdir -p ~/.codex/skills
cp -R Wireless-Bib-Style ~/.codex/skills/ieee-bib-style-audit
```

Restart Codex after installation. Then invoke the skill with:

```text
[$ieee-bib-style-audit]
Audit my references.bib against the wireless IEEE style.
```

## Usage

For read-only audits, ask Codex to inspect a `.bib` file and report entries that do not match the style. For cleanup, explicitly ask Codex to modify the file. The skill preserves citation keys by default and avoids guessing missing metadata such as DOI, pages, issue, or conference location.

---

# Wireless Bib Style 中文说明

## 描述

Wireless Bib Style 是一个 Codex skill，用来按照无线通信论文常用的 IEEE 参考文献模板检查和轻量规范 BibTeX 文件。它可以帮助统一作者姓名缩写、IEEE 期刊缩写、会议 `Proc.` 写法、月份和地点字段、arXiv 条目格式，以及重复 citation key。

## 介绍

本仓库包含：

- `SKILL.md`：Codex skill 的主说明文件。
- `template.bib`：IEEE BibTeX 字符串和格式模板。
- `references/style-rules.md`：检查规则、常见问题和推荐条目形态。
- `agents/openai.yaml`：Codex 中显示用的简短提示配置。

这个 skill 面向本地论文风格，不把所有 BibTeX 差异都判成错误。它会先根据 `template.bib` 或用户指定的标准 `.bib` 推断目标格式，再把明确问题和需要人工判断的风格选择分开报告。

## 安装

直接克隆到 Codex skills 目录：

```bash
mkdir -p ~/.codex/skills
git clone https://github.com/Elapsedf/Wireless-Bib-Style.git ~/.codex/skills/ieee-bib-style-audit
```

如果已经把仓库克隆到其他位置，可以复制到 skills 目录：

```bash
mkdir -p ~/.codex/skills
cp -R Wireless-Bib-Style ~/.codex/skills/ieee-bib-style-audit
```

安装后重启 Codex。使用时可以这样触发：

```text
[$ieee-bib-style-audit]
帮我检查 references.bib 是否符合 wireless IEEE bibliography style。
```

## 使用方式

如果只是检查，要求 Codex 只报告 `.bib` 文件中的不一致条目。如果需要实际修改，明确说“帮我修复”或“直接改”。默认情况下，skill 会保留 citation key，并且不会凭记忆补全 DOI、页码、期号、会议地点等缺失信息。
