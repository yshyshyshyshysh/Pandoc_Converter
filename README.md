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

### Alternative way: no pandoc
後來發現用 VScode 上的套件比較快: [Markdown PDF](https://blog.darkthread.net/blog/markdown-to-pdf/)

### Steps

**Step 1. Install the latest pandoc**
-   See the above.

**Step 2. Install a LaTeX distribution**
-  (Not recommended) Download the network install from the official website: [TeX Live](https://www.tug.org/texlive/quickinstall.html) (it involves downloading and installing required files from the source server, which may take several hours).
-  (Recommended) Download the pre-packaged installation image (*.iso) at once:<br>
    -  Enter [清华大学镜像站](https://mirrors.tuna.tsinghua.edu.cn/CTAN/systems/texlive/Images/) and download `texlive2024.iso`<br>
    -  Open the downloaded ISO file and double-click `install-tl-windows.bat` to install.

**Step 3. Find a valid Chinese font (if the document has Chinese)**
-   Run in cmd to see the available Chinese font: `fc-list :lang=zh`<br>
  The font name follows the font file location. For example, `C:/WINDOWS/Fonts/mingliu.ttc: MingLiU,細明體:style=Regular`, font name is called MingLiU.
-   Or download more fonts: [Google Fonts](https://fonts.google.com/) / [DaFont](https://www.dafont.com/)

**Step 4. Set styling for the output pdf`**
-   Download the `head.tex` into the same folder with your `input.md` to render document styles.

```tex {.linenums}
\usepackage{fancyvrb,newverbs}
\usepackage{hyperref}
\usepackage[top=2cm, bottom=1.5cm, left=2cm, right=2cm]{geometry}

% change background color for inline code
\definecolor{bgcolor}{HTML}{E0E0E0}
\let\oldtexttt\texttt
\renewcommand{\texttt}[1]{
  \colorbox{bgcolor}{\oldtexttt{#1}}
}

%% color and other settings for hyperref package
\hypersetup{
  bookmarksopen=true,
  linkcolor=blue,
  filecolor=magenta,
  urlcolor=RoyalBlue,
}
```
-   Or download an existing LaTeX template: follow [how to set up Latex template](https://sam.webspace.tw/2020/01/13/%E4%BD%BF%E7%94%A8%20Pandoc%20%E5%B0%87%20Markdown%20%E8%BD%89%E7%82%BA%20PDF%20%E6%96%87%E4%BB%B6/)

**Step 5. Run in cmd: `pandoc "input_file.format" -o "input_file.format" --pdf-engine=xelatex -V mainfont='font_name'`**
-   Convert Markdown to PDF using custom styling:<br>
  `pandoc README.md -o README.pdf --pdf-engine=xelatex -V CJKmainfont='PMingLiU' -V mainfont='Times New Roman' -H head.tex`
-   Convert Markdown to PDF using an existing template (Eisvogel is used here):<br>
  `pandoc README.md -o README.pdf --pdf-engine=xelatex -V CJKmainfont='PMingLiU' -V mainfont='Times New Roman' --from markdown --template eisvogel --listings`


### Reference
About TeX Live installation
-   [Pandoc with Chinese](https://github.com/jgm/pandoc/wiki/Pandoc-with-Chinese)
-   [安裝 TeX Live 镜像](https://zhuanlan.zhihu.com/p/64555335)

About rendering styles in TeXLive
-   [Eisvogel: pandoc-latex-template](https://github.com/Wandmalfarbe/pandoc-latex-template)
-   [customizing-pandoc](https://breezetemple.github.io/2020/11/02/customizing-pandoc/)


<!-- 
-   [head.tex 中的指令 1](https://zhuanlan.zhihu.com/p/444440478)
-   [head.tex 中的指令 2](https://jdhao.github.io/2017/12/10/pandoc-markdown-with-chinese/)
--!>
