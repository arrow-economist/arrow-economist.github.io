---
title: vscode로 latex 작업 시 bibliography 에러 문제 해결 방법
author: arrow
date: 2024-07-26 04:04:00 +0800
categories: [latex]
tags: [latex]
---

# #latex #natbib
요즘은 이제 논문을 쓰고 있는데, overleaf도 좋지만 버전 기록을 위해서 vscode로 작성하고 깃허브에 올려두는 방식으로 활용하고 있다. vscode로 latex를 쓰는 데 불편함이 없지만 bibliography를 natbib을 이용해서 작성할 때 계속 에러가 떴다. `\citet{author}` 이런 식으로 cite를 해도 `?`만 떴는데 해결하는 방법을 알아내서 기록하려고 한다.

### 해결 방법
일단 문제는 `Undefined citations` 문제다. 예를 들어서
`"message": "Citation 'abadieetal2010' on page 1 undefined.`
이런 식으로 메시지가 뜨는 문제이다.

해결방법은 의외로 간단했는데,vscode 상에서 tex 탭에 들어가면
`Build LaTeX project`라는 토글이 보인다.
열면, `Recipe: pdflatex -> bibtex -> pdflatex*2`라는게 보이는데
이걸 실행해주면 된다.
그러면 이 에러가 뜨지 않게 된다.
원인은 bibtex를 자동적으로 업데이트?를 시켜주지 않아서 그런다는데
이걸 일일이 눌러야한다면 여간 귀찮은 일이 아니라 overleaf를 쓸 것 같다.

혹시 자동으로 실행을 시켜서 계속 귀찮게 하지 않는 방법을 알게 되면 다시 이 글에 수정해서 작성해보도록 하겠다.
