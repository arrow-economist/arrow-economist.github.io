---
title: latex bibliography 설정 팁 feat. natbib
author: arrow
date: 2024-05-01 19:35:00 +0800
categories: [latex]
tags: [latex]
---

# #latex #natbib

내 분야는 latex으로 논문을 쓴다. 이제 latex도 쓴 지 4~5년이 되어가서 그런지 어느 정도 적응은 했지만, 여전히 서지관리를 하는 부분은 어렵다. term paper를 쓰면서 bibliography를 관리하는 방법을 찾아봤는데, 이걸 정리해보고자 한다.

### package: natbib

[Overleaf 공식 문서](https://www.overleaf.com/learn/latex/Bibliography_management_with_natbib)에 따르면 `natbib`은 citation 중 특히 author-year scheme 등을 커스터마이징 하는데에 특화된 패키지라고 한다. bibliography를 위한 패키지는 `biblatex`, `bibtex` 등이 있는데 내가 쓰는 스타일은 결국 `natbib`을 써야한다는 것을 알았다.

```latex
\usepackage[]{natbib}
\bibliographystyle{plainnat}
\begin{document}
\bibliography{bibs.bib}
\end{document}
```

우선 기본적인 사용 방법은 다음과 같다. `usepackage`로 사용을 하는데, 큰괄호 `[]` 안에는 다양한 옵션을 넣을 수 있다. 그리고 `begin{document}` 전에 `\bibliographystyle{}`을 이용해서 reference style을 설정할 수 있다. 마지막에 reference가 들어가는 부분에는 `\bibliography{.bib}`을 입력해서 reference 섹션을 삽입할 수 있다.

#### `\usepackage[]{natbib}`

| Option                              | Meaning                                                                                         |
| ----------------------------------- | ----------------------------------------------------------------------------------------------- |
| `round`, `square`, `curly`, `angle` | `\cite{}` 시 괄호 옵션. `(round; default)` , `[square]`, `{curly}`, `<angle>`                   |
| `colon`, `comma`                    | 여러 개의 citation을 구분하는 마크                                                              |
| `authoryear`, `numbers`, `super`    | `\cite{}` 시 `저자 연도`, `숫자`, `윗첨자`로 하는 citation 스타일                               |
| `sort`, `sort&compress`             | 여러 개의 citation이 cite된 순서에 따라 그대로 정렬을 하는지, 그리고 그 citation들을 압축하는지 |
| `longnamefirst`                     | 저자가 셋 이상인 경우 `et al.`로 압축 된다                                                      |

`\usepackage[round, authoryear, longnamefirst]{natbib}`과 같이 입력하는 경우, 만약 `\citet{Corradoetal2009}`와 같이 cite를 한다면 `Corrado et al. (2009)`와 같이 print가 된다. (`Corradoetal2009`는 내가 저장한 bib name이고 이 논문의 경우는 저자가 3명이다.) 이 때 `\citet`는 `\cite`와는 다르게 `author (year)`의 방식으로 출력을 해주는 장점이 있다. 내 분야의 경우는 거의 `author (year)`로 나타내기 때문에 `\citet{}`를 쓰는게 맞다.

#### `\bibliographystyle{}`

Reference 섹션에서의 스타일을 설정하는 부분이다. 여기에는 `plainnat`, `unsrtnat`, `abbrvnat` 정도가 있는데, `plainnat`은 alphabetical order로 정렬을 해주면서 저자의 풀네임을 적는 형식이다. `unsrtnat`은 cite가 된 순서대로 정렬을 해주고 풀네임을 적는 형식이다. `abbrvnat`은 alphabetical order로 정렬을 하되, 저자의 first name은 줄이는 방식이다. 나의 분야의 경우에는 `plainnat`이나 `abbrvnat`을 쓰는게 맞아 보이는데, 아마 저널에 따라서 약간의 스타일의 차이가 있을 것이다.

#### `\bibliography{bibs.bib}`

이걸 `\end{document}` 전에 삽입을 하면 해당 위치에 reference 섹션을 넣을 수 있다.

### `.bib` 파일 관리 팁

논문을 검색하면 구글 스칼라든, 아니면 어떤 저널 홈페이지든 간에 export citation을 하는 버튼이 있다. 누르면, `bibtex`와 같은 형식으로 출력하는 방법이 있는데, 이걸 누르면

```latex
@Article{Corradoetal2009,
  author={Carol Corrado and Charles Hulten and Daniel Sichel},
  title={{Intangible Capital And U.S. Economic Growth}},
  journal={Review of Income and Wealth},
  year=2009,
  volume={55},
  number={3},
  pages={661-685},
  month={September},
  keywords={},
  doi={10.1111/j.1475-4991.2009.}
}
```

와 같이 복사 붙여넣기, 혹은 파일을 저장하는 형식으로 불러올 수 있다. 이걸 `bibs.bib` (파일 명은 아무렇게나 설정 가능)와 같은 `.bib` 파일에 붙여넣기를 하거나 overleaf를 사용하는 경우는 파일을 끌어오거나 하는 형식으로 레퍼런스를 관리하면 된다. 여기에서 첫번째 항목이 내가 `\citet{}`를 할 때 불러올 단축어이기 때문에 본인이 알아보기 쉬운 이름으로 설정하면 된다.

### Reference

[Overleaf 공식문서(bibliography style)](https://www.overleaf.com/learn/latex/Natbib_bibliography_styles)\
[Overleaf 공식문서(natlib)](https://www.overleaf.com/learn/latex/Bibliography_management_with_natbib#Reference_guide)\
[Wikipedia](https://en.wikibooks.org/wiki/LaTeX/Bibliography_Management)
