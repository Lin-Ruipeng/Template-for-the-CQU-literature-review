# 重庆大学文献综述 LaTeX 模板

主文件是 `cqu_literature_review.tex`，使用 XeLaTeX 编译。模板已按你导出的 PDF 设置：A4、左右 1.25 英寸、上下 1 英寸；正文宋体/Times New Roman 小四号、固定 20 磅、首行缩进 2 字符；一级标题为左对齐的 `1．引言` 形式，二级/三级标题和图表/公式编号规则也已写入源码。

参考文献已经改为现行 **GB/T 7714—2025** 的理工科顺序编码制。正文中第一次出现的 `\cite{...}` 决定编号和文后顺序；连续编号会自动压缩为 `[1-3]`。模板示例中的引用行只是演示，定稿时应替换为正文中的实际引用。

## 在 MiKTeX 中编译

在当前文件夹打开 PowerShell：

```powershell
xelatex cqu_literature_review.tex
```

模板已默认在最后新起一页输出参考文献。定稿时删除示例条目、替换为自己的文献，并确保每一条文后参考文献都在正文中用 `\cite{文献键}` 实际引用；不要使用 `\nocite{*}` 代替正文引用。

编译时运行：

```powershell
xelatex cqu_literature_review.tex
biber cqu_literature_review
xelatex cqu_literature_review.tex
xelatex cqu_literature_review.tex
```

正式写作时，删除示例条目，使用 `\cite{文献键}` 引用自己的文献，并保留 `references.bib` 中与国标类型相对应的字段。

## 使用提示

- `\reviewchapter{...}`：一级标题，自动生成左对齐的 `1．标题`、`2．标题` 等章节号。
- `\reviewsection{...}`：二级标题，自动生成 `1.1`、`1.2` 等编号。
- `\reviewsubsection{...}`：三级标题，自动生成 `1.1.1` 等编号。
- 图题写在 `figure` 环境内部、图之后；表题写在 `table` 环境内部、表格之前；公式使用 `equation` 环境即可自动右对齐编号。
- 参考文献驱动已覆盖图书 `[M]`、图书析出文献 `[M]`、期刊 `[J]`、会议录 `[C]`、学位论文 `[D]`、报告 `[R]`、标准 `[S]`、专利 `[P]`、网站/网页 `[EB/OL]`、数据集 `[DS/OL]`、软件 `[CP/OL]` 和预印本 `[PP/OL]` 等常用类型；电子资源会按 `URL` 自动标记为 `/OL`，也可在条目中用 `usera = {OL}` 明确指定其他载体代码。
- 参考文档的格式说明要求定稿前删除指导文字；模板中对应的“格式要求”段落已标注为删除提示，提交前请删除或注释。

## 字体说明

导出的参考 PDF 实际嵌入的标题字体为 Microsoft YaHei；电脑中已有 `C:\Windows\Fonts\msyh.ttc`，模板会直接调用 `Microsoft YaHei`。正文使用 SimSun，标题使用 SimHei，西文使用 Times New Roman。

参考 PDF 无页眉、页脚、页码、图、表、公式或目录；模板默认不输出这些元素，但会在最后新页输出参考文献列表。参考文献标点和文献类型/载体标识按 GB/T 7714—2025 设置，而不是沿用 PDF 示例中的中文全角标点。
