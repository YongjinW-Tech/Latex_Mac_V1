# LaTeX_Mac_V1

一个面向课程论文、学术论文写作的 LaTeX 模板（按照深圳大学研究生课程论文的相关格式文件），适配 Mac 系统，内置较为完整的**页面格式**、**评分表**、**诚信承诺书**、**封面**、**目录**与**参考文献**自动化排版，符合中文高校常用论文排版规范。

## 📂 项目结构说明
``` shell
Latex_Mac_V1/
│
├── template.tex                    # 主文件，编译入口
├── reference.bib                   # 参考文献库（BibTeX 格式）
├── gbt7714-numerical.bst           # 国标参考文献样式文件（数字引用格式）
├── gbt7714.sty                     # 国标参考文献样式定义文件
├── Sections/                       # 各章节内容文件
│   ├── score_sheet.tex             # 评分表
│   ├── letter_of_commitment.tex    # 学术诚信承诺书
│   ├── score_sheet_cover.tex       # 课程论文封面
│   ├── abstract.tex                # 摘要
│   ├── 1-Introduction.tex          # 引言
│   ├── 2-Content.tex               # 正文内容
│   └── 3-Conclusion.tex            # 结论
├── Fonts/                          # 字体
├── Imgs/                           # 图片
└── .gitignore                      # Git 忽略规则
```

## 📖 功能特点

- ✅ 完整封面、评分表、诚信承诺书模板
- ✅ 自动目录与分页设置
- ✅ 页眉页脚美化，自动统计总页数
- ✅ 行距、段落格式、字号符合学术规范
- ✅ 兼容 `gbt7714` 中文参考文献格式（符合国标 GB/T 7714-2015）
- ✅ Mac 平台字体适配（Times New Roman）

## 🚀 编译方法

### 方式一：使用 VSCode + LaTeX Workshop 插件

1. 安装 TeX 完整发行版（含所有宏包）：

2. 安装 VSCode 插件：
    - LaTeX Workshop

3. 直接用 VSCode 打开项目根目录，编译 `template.tex`。

### 方式二：命令行编译

确保你已安装完整的 TeX 环境后，执行：

```bash
xelatex template.tex
biber template
xelatex template.tex
xelatex template.tex
```

### VSCode 配置建议（重要）
为了确保 LaTeX Workshop 插件可以顺利完成完整编译，建议在 VSCode 的 settings.json 中添加以下配置：
```python
"latex-workshop.latex.tools": [
  {
    "name": "latexmk",
    "command": "latexmk",
    "args": [
      "-synctex=1",
      "-interaction=nonstopmode",
      "-file-line-error",
      "-pdf",
      "%DOC%"
    ]
  },
  {
    "name": "xelatex",
    "command": "xelatex",
    "args": [
      "-synctex=1",
      "-interaction=nonstopmode",
      "-file-line-error",
      "%DOC%"
    ]
  },
  {
    "name": "pdflatex",
    "command": "pdflatex",
    "args": [
      "-synctex=1",
      "-interaction=nonstopmode",
      "-file-line-error",
      "%DOC%"
    ]
  },
  {
    "name": "bibtex",
    "command": "bibtex",
    "args": [
      "%DOCFILE%"
    ]
  }
],
"latex-workshop.latex.recipes": [
  {
    "name": "xelatex -> bibtex -> xelatex*2",
    "tools": [
      "xelatex",
      "bibtex",
      "xelatex",
      "xelatex"
    ]
  },
  {
    "name": "xelatex",
    "tools": [
      "xelatex"
    ]
  },
  {
    "name": "latexmk",
    "tools": [
      "latexmk"
    ]
  },
  {
    "name": "pdflatex -> bibtex -> pdflatex*2",
    "tools": [
      "pdflatex",
      "bibtex",
      "pdflatex",
      "pdflatex"
    ]
  }
]
```
**推荐使用 xelatex -> bibtex -> xelatex*2 方案，可正确处理中文和参考文献**.

## ⚠️ 注意事项
- **Fonts 目录不建议纳入仓库**：模板内已配置系统字体，使用者无需上传本地字体文件。
- **额外字体支持**：若需要额外字体支持，请在 `template.tex` 文件中自行修改 `\setmainfont` 配置。
- **章节内容管理**：所有章节内容放置在 `Sections/` 文件夹内，按需修改对应 `.tex` 文件即可。
- **参考文献编辑**：请编辑 `reference.bib` 文件以添加或修改参考文献条目。


## 版权说明

本模板仅供学习与课程论文撰写参考使用，使用者请遵循学术诚信规范。