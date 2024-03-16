# Convert File Formats Using Pandoc
**`January 30, 2024 / by Yu-Shin, Hu`**

Mathematical formulas and pictures can be converted successfully!
- [Convert Latex to other formats](#convert-latex-to-other-formats)
- [Convert other formats to PDF](#convert-other-formats-to-pdf)


## Convert Latex to other formats

### Steps

**Step 1. Install the latest pandoc**
-   [Pandoc installer](https://pandoc.org/installing.html)
-   For Windows system, download pandoc-3.1.11-windows-x86_64.msi

**Step 2. Run in cmd: `pandoc -s "input_file.format" -o "output_file.format"`**
-   Remember to assign desired filename extension behind the input & output files
-   Convert Latex to Word: `pandoc -s "input_file.tex" -o "output_file.docx"`
-   Convert Latex to Markdown: `pandoc -s "input_file.tex" -o "output_file.md"`

## Convert other formats to PDF

### Steps

**Step 1. Install the latest pandoc**
-   See the above.

**Step 2. Install a LaTeX distribution**
-  [TeX Live](https://www.tug.org/texlive/quickinstall.html) 

**Step 3. Find a valid Chinese font**
-   Run in cmd to see the available Chinese font: `fc-list :lang=zh`
-   Or download more fonts: [Google Fonts](https://fonts.google.com/) / [DaFont](https://www.dafont.com/)

**Step 2. Run in cmd: `pandoc  "input_file.format" -o "input_file.format" --pdf-engine=xelatex -V mainfont='font_name'`**
-   The font name follows the font file location. For example, `C:/WINDOWS/Fonts/mingliu.ttc: MingLiU,細明體:style=Regular`, font name is called MingLiU.
-   Convert Markdown to PDF:<br>
  `pandoc  "input_file.md" -o "output_file.pdf" --pdf-engine=xelatex -V mainfont='MingLiU'`


### Reference
-   [Pandoc with Chinese](https://github.com/jgm/pandoc/wiki/Pandoc-with-Chinese)
-   [使用 Pandoc 把 Markdown 转为 PDF 文件](https://jdhao.github.io/2017/12/10/pandoc-markdown-with-chinese/)

