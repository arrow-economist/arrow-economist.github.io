---
title: 맥에서 vscode에서 latex 편집하기 feat. LaTeX Workshop
author: arrow
date: 2024-03-06 10:18:00 +0800
categories: [latex]
tags: [latex]
---

# #VScode #LaTeX

나는 보통 LaTeX 편집을 Overleaf에서 한다. Overleaf는 레이텍을 편집할 수 있게 해주는 온라인 편집툴인데, 무료로도 충분히 많은 기능들을 활용할 수 있고 간단해서 많은 사람들이 이용한다. 그런데 VScode에서 LaTeX를 한 번 써보고 싶어서 익스텐션을 찾아보았다.

## LaTeX Workshop

[LaTeX Workshop](https://github.com/James-Yu/LaTeX-Workshop/wiki/Install)은 수많은 VScode LaTeX들 중에서 가장 많이 다운로드 된 확장프로그램으로 보인다. (확실하진 않음). 그런데 익스텐션만 깔면 되는 줄 알았더니 은근 복잡하고 찾아도 잘 나오지 않아서 내가 해결한 방법을 기록해보려고 한다.

우선 VScode에서 LaTeX Workshop을 검색해서 설치해준다. 이 상태에서는 `~.tex`파일을 만들어서 써도 컴파일이 되지 않는다. 이 때는 몇 가지 세팅만 해주면 되는데, 나의 경우는 macOS를 사용 중이므로 맥 기반으로 설명을 하겠다.

### 1. MacTeX 설치하기

우선 LaTeX Workshop 가이드에도 나와있듯, **"The only requirement is a compatible LaTeX distribution in the system PATH."** 를 위해서 **TeX Live** 를 설치하면 된다. 맥에서는 **MacTeX**를 설치하면 된다.

[MacTeX 홈페이지](https://www.tug.org/mactex/mactex-download.html)에 들어가서 설치하거나 homebrew를 사용중이라면

```zsh
brew install --cask mactex
```

를 터미널에 입력해서 설치하면 된다. 설치 후 `/Applications/TeX`에 들어가서 `Tex Live Utility`와 `TeXShop`을 실행해 잘 설치가 되었는지 확인을 해준다.

### 2. settings.json 손대기

알맞게 설치가 되었다면 이제 vscode 세팅 파일을 조금만 수정해주면 된다.  
Note: [참고한 사이트](https://hackmd.io/@x5758x/maclatex)

우선 vscode를 실행해주고 `cmd+shift+p`를 눌러서 커맨드 팔레트에서 `Preferences: Open User Settings (JSON)`을 들어가준다.

그러면 제일 바깥의 `{}` 괄호에 다음을 추가해주면 된다. 나의 경우는 맨 마지막에 `}` 직전에 넣어줬다.

```json
"latex-workshop.bibtex-format.sort.enabled": true,
  "latex-workshop.bibtex-format.align-equal.enabled": true,
  "latex-workshop.bibtex-format.sortby": [
    "booktitle",
    "journal",
    "title",
    "year",
  ],
  "latex-workshop.bibtex-fields.sort.enabled": true,
  "latex-workshop.bibtex-fields.order": [
    "title",
    "author",
    "key",
    "booktitle",
    "journal",
    "year",
    "volume",
    "number",
    "pages",
    "publisher",
    "address",
    "editor",
    "edition",
    "translator",
  ],
  "latex-workshop.intellisense.package.enabled": true,
  "latex-workshop.latex.autoClean.run": "onBuilt",
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
  "latex-workshop.latex.recipe.default": "pdflatex*2",
  "latex-workshop.latex.recipes": [
    {
      "name": "pdflatex*2",
      "tools": [
        "pdflatex",
        "pdflatex"
      ]
    },
    {
      "name": "xelatex*2",
      "tools": [
        "xelatex",
        "xelatex"
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
    },
    {
      "name": "xelatex -> bibtex -> xelatex*2",
      "tools": [
        "xelatex",
        "bibtex",
        "xelatex",
        "xelatex"
      ]
    },
  ],
  "latex-workshop.latex.tools": [
    {
      "name": "xelatex",
      "command": "xelatex",
      "args": [
        "-synctex=1",
        "-interaction=nonstopmode",
        "-file-line-error",
        "-pdf",
        "-outdir=%OUTDIR%",
        "%DOC%"
      ],
      "env": {}
    },
    {
      "name": "pdflatex",
      "command": "pdflatex",
      "args": [
        "-synctex=1",
        "-interaction=nonstopmode",
        "-file-line-error",
        "%DOC%"
      ],
      "env": {}
    },
    {
      "name": "bibtex",
      "command": "bibtex",
      "args": [
        "%DOCFILE%"
      ],
      "env": {}
    }
  ],
  "latex-workshop.message.badbox.show": false,
  "latex-workshop.synctex.afterBuild.enabled": true,
  "latex-workshop.view.pdf.internal.synctex.keybinding": "double-click",
  "latex-workshop.view.pdf.viewer": "tab"
```

이걸 추가 후 저장하면 이제 `.tex`파일을 만들면 컴파일이 잘 되는 것을 확인할 수 있다.

## LaTeX 자동 컴파일 시간

나는 자동보다 수동으로 컴파일 하는 것을 선호하는데, 그 이유는 수식을 작성하려고 `$`을 열어놓거나 하는 경우 자동으로 컴파일 되면 에러가 생기기 때문이다. 이 익스텐션은 1초마다 자동 컴파일을 하도록 디폴트가 설정되어 있었다. 따라서 나는 60초에 한 번 되도록 수정을 해줬다.

`LaTeX Workshop`의 `Extension Settings`에 들어가서 `Auto build: interval`쪽으로 가면 `1000`이 기본 값일텐데 이를 입맛에 맞게 변경해주면 된다. 나는 `60000` (60초)로 설정을 해두었다.

이제는 오프라인에서도 LaTeX를 쓸 수 있게 되었다!