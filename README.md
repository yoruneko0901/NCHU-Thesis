## 簡介

本專案使用 LaTeX 編寫論文，符合國立中興大學學位論文格式規範中的標準。專案的結構設計便於管理論文的不同部分，使得撰寫、維護和更新論文內容更加高效。

## 主文件 (main.tex)

`main.tex` 是此專案的核心文件，它統籌了整個論文的結構。以下是 `main.tex` 的主要功能：

- 定義論文的排版格式，如字體、行距、頁邊距等。
- 論文的不同章節、附錄等內容通過 `\include{}` 指令導入各自的獨立文件。
- 自動生成目錄、表目次、圖目次等。

`main.tex` 文件包含了整篇論文的框架，引用了其他拆分文件來完成具體內容的填充。

## 拆分文件

各個拆分文件負責包含論文的具體內容或特定部分。這些文件被 `main.tex` 引用，使得每個部分的內容更加獨立和模組化。以下是各拆分文件的用途說明：

- **`ThesisTitle.tex`**: 包含論文的標題頁內容，包括論文題目、作者、指導教授等資訊。
- **`Examine.tex`**: 審核頁面，包含口試委員、指導教授的簽名頁。
- **`Authority.tex`**: 授權頁，記錄論文的授權資訊。
- **`ChineseAbstract.tex`**: 中文摘要，包含論文的研究動機、方法、結果等摘要內容。
- **`EnglishAbstract.tex`**: 英文摘要，與中文摘要內容相對應的英文描述。
- **`Chapter1.tex`**: 第一章的內容。
- **`Chapter2.tex`**: 第二章的內容。
- **`Chapter3.tex`**: 第三章的內容。
- **`References.tex`**: 參考文獻列表。
- **`AppendixA.tex`**: 附錄A的內容。

這些拆分文件通過 `\include{}` 指令被主文件 `main.tex` 包含在內，使得論文的各個部分得以組織和管理。

## 注意事項

- 在編寫各章節和附錄時，請確保格式遵循學校的格式規範，詳細規範請參考文件 `F2-65學位論文格式規範-中文版.pdf`。
- 修改某一章節的內容時，只需更新對應的拆分文件，重新編譯 `main.tex` 即可生成更新後的論文。

## 如何使用

1. [下載Tex Live](https://mirror.ctan.org/systems/texlive/tlnet/install-tl-windows.exe) (要下載很久)
安裝完成後在終端機分別輸入，看到版本訊息有輸出就算安裝成功
```ps
tex -v
latex -v
xelatex -v
pdflatex -v
tlmgr info ctex
```

2. vscode中安裝 LaTeX Workshop

3. 編輯vscode的設定
在settings.json中新增以下設定
```json
  "latex-workshop.latex.tools": [
        {
          "name": "xelatex",
          "command": "xelatex",
          "args": [
              "-synctex=1",
              "-interaction=nonstopmode",
              "-file-line-error",
              "%DOCFILE%"
          ]
      },
      {
        "name": "lualatex",
        "command": "lualatex",
        "args": [
            "-synctex=1",
            "-interaction=nonstopmode",
            "-file-line-error",
            "-output-directory=%OUTDIR%",           
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
      }
  ],
  "latex-workshop.latex.recipes": [
      {
          "name": "xelatex",
          "tools": [
              "xelatex"
          ]
      },
      {
          "name": "lualatex",
          "tools": [
              "lualatex"
          ]
      },
      {
          "name": "pdflatex",
          "tools": [
              "pdflatex"
          ]
      }
  ],
  "latex-workshop.view.pdf.viewer": "tab",
    
  "latex-workshop.latex.clean.enabled": true,
  "latex-workshop.latex.clean.fileTypes": [
    "*.aux",
    "*.bbl",
    "*.blg",
    "*.idx",
    "*.ind",
    "*.lof",
    "*.lot",
    "*.out",
    "*.toc",
    "*.acn",
    "*.acr",
    "*.alg",
    "*.glg",
    "*.glo",
    "*.gls",
    "*.ist",
    "*.fls",
    "*.log",
    "*.fdb_latexmk"
  ],
```
4. 使用 `git clone https://github.com/yoruneko0901/NCHU-Thesis.git` 下載本專案
5. 點擊編譯
![image](https://github.com/user-attachments/assets/3138d1d1-7c88-4770-88e0-5acda13f2b0a)
6. 查看編譯好的檔案
![image](https://github.com/user-attachments/assets/fb85493f-5acb-4a60-8606-8698282b9e36)
