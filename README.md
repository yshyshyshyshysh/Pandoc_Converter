# Convert File Formats Using Pandoc
**`January 30, 2024 / by Yu-Shin, Hu`**

Mathematical formulas and pictures can be converted successfully!

## Steps <br>

**Step 1. Download the latest pandoc installer**
-   Their website: https://pandoc.org/installing.html
-   For Windows system, download pandoc-3.1.11-windows-x86_64.msi

**Step 2. Run in cmd: `pandoc -s "input_file" -o "output_file"`**
-   Remember to assign desired filename extension behind the input & output files
-   Convert Latex (.tex) to Word (.docx): `pandoc -s "input_file.tex" -o "output_file.docx"`
-   Convert Latex (.tex) to Markdown (.md): `pandoc -s "input_file.tex" -o "output_file.md"`
