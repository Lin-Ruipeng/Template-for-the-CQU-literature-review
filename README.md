# 重庆大学文献综述 LaTeX 模板

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

这是一个面向重庆大学本科生、研究生的中文文献综述 LaTeX 模板。项目依据仓库中的 Word/PDF 版格式参考文件整理，重点适配理工科常用的 XeLaTeX + Biber 工作流。

> 本项目是个人整理的开源模板，不是重庆大学官方发布的软件包或格式类文件。提交论文前，请以所在学院、专业和研究生管理系统发布的最新要求为准。

## 功能概览

- 使用 A4 纸张和参考文档中的页边距设置；
- 显式调用中文和西文字体，减少不同电脑上的字体漂移；
- 提供一级、二级、三级标题命令，自动生成规范编号；
- 支持图、表、公式按章节编号；
- 使用 Biber 管理参考文献，采用理工科常用的顺序编码制；
- 附带可直接编译的示例 PDF、`references.bib` 和 Word/PDF 格式参考文件；
- 通过 `.gitignore` 排除 LaTeX 编译产生的临时文件。

## 快速开始

### 环境要求

- Windows；
- [MiKTeX](https://miktex.org/)；
- XeLaTeX；
- Biber；
- 中文字体：SimSun（宋体）、SimHei（黑体）、KaiTi（楷体）或等价字体；
- 西文字体：Times New Roman。

MiKTeX 安装完成后，建议打开 MiKTeX Console 更新宏包，并确认 `xelatex` 和 `biber` 已加入 PATH。模板使用 XeLaTeX，不要用 `pdflatex` 编译。

### 编译模板

在仓库根目录打开 PowerShell，按以下顺序执行：

```powershell
xelatex -interaction=nonstopmode cqu_literature_review.tex
biber cqu_literature_review
xelatex -interaction=nonstopmode cqu_literature_review.tex
xelatex -interaction=nonstopmode cqu_literature_review.tex
```

最终文件为 `cqu_literature_review.pdf`。如果只修改正文而没有新增或修改引用，通常仍建议完整执行上述四步，以确保目录、引用和参考文献页保持同步。

## 文件结构

| 文件 | 作用 |
| --- | --- |
| `cqu_literature_review.tex` | 主文档，正文和版式设置均在此文件中 |
| `references.bib` | BibTeX 文献数据库示例 |
| `cqu_literature_review.pdf` | 当前模板的编译示例 |
| `文献综述正文模板.docx` | 格式参考 Word 文档 |
| `文献综述正文模板.pdf` | 格式参考 PDF 文档 |
| `.gitignore` | 排除 LaTeX 辅助文件 |
| `LICENSE` | 项目许可证 |

## 写作方法

### 标题

使用模板提供的命令，不建议手动输入章节号：

```latex
\reviewchapter{引言}
\reviewsection{研究背景}
\reviewsubsection{国内外研究现状}
```

上述命令分别生成一级、二级和三级标题，编号形式为 `1．标题`、`1.1 标题` 和 `1.1.1 标题`。

### 图、表和公式

图题放在图下方，表题放在表上方；公式使用标准 `equation` 环境：

```latex
\begin{equation}
  y = ax+b
\end{equation}
```

模板会按一级标题自动生成图、表和公式编号。正式提交前请删除示例图表和文档中的格式提示文字。

### 参考文献

参考文献使用顺序编码制，正文第一次引用的顺序决定文后编号：

```latex
近年来，相关方法得到了广泛研究\cite{tang2019,qin2017}。
```

当前模板按现行 [GB/T 7714—2025](https://openstd.samr.gov.cn/bzgk/std/newGbInfo?hcno=C6CE52E55AC09B9C79A20AEA77CEDD14) 的顺序编码制组织参考文献。`references.bib` 中提供了图书、期刊、会议论文、学位论文和电子资源等示例。

正式写作时请注意：

1. 用真实文献替换 `references.bib` 中的示例条目；
2. 每条文后文献都应在正文中通过 `\cite{文献键}` 实际引用；
3. 不要使用 `\nocite{*}` 代替正文引用；
4. 检查作者、题名、出版地、出版社、年份、卷期、页码、URL 和访问日期等字段；
5. 定稿前按照学院的具体要求核对文献类型标识、外文文献比例和电子资源著录信息。

## 字体与兼容性

模板默认调用 Windows 常见字体：正文中文使用 SimSun，标题中文使用 SimHei，中文斜体回退到 KaiTi，西文使用 Times New Roman。若出现字体缺失，优先在 MiKTeX 之外检查 Windows 字体是否安装，再修改 `cqu_literature_review.tex` 中的字体设置。

导出的参考 PDF 不包含页眉、页脚、页码、目录、图和表，因此本模板默认不输出这些元素；参考文献会在文末新起一页输出。

## 提交前检查清单

- [ ] 删除示例正文、示例引用和格式提示文字；
- [ ] 使用真实研究内容替换摘要和章节内容；
- [ ] 运行完整的 XeLaTeX → Biber → XeLaTeX → XeLaTeX 编译流程；
- [ ] 检查 PDF 中是否存在未定义引用、空参考文献表或字体替换；
- [ ] 按学院最新要求核对页边距、字号、标题间距和参考文献格式；
- [ ] 不要提交 `.aux`、`.bbl`、`.bcf`、`.blg`、`.log` 等编译临时文件。

## 参与贡献

欢迎通过 GitHub Issue 反馈格式问题、编译问题或改进建议，也欢迎提交 Pull Request。提交修改时请尽量同时更新源文件、示例 PDF 和 README，并说明所依据的格式要求或复现步骤。

## 许可证与参考文件说明

本项目模板代码、示例配置和说明文档按照仓库中的 MIT License 发布。

仓库中的 Word/PDF 格式参考文件来自学校相关材料，仅用于说明和对照排版；其著作权、使用范围及再分发权限以原发布方的规定为准，不因项目采用 MIT License 而自动转授权。
