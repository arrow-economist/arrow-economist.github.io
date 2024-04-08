---
title: latex mathbb에 숫자 넣을 때 팁
author: arrow
date: 2024-04-07 11:38:00 +0800
categories: [latex]
tags: [latex]
---

# #latex

LaTeX로 수식을 입력하다보면 `\mathbb`를 쓰는 일이 종종 있다. Expectation을 취할 때 $\mathbb{E}$와 같이 쓴다거나, indicator function을 쓸 때 등등의 경우가 그렇다. 하지만 `\mathbb`에 숫자를 집어넣으면 제대로 써지지 않거나 이상한 기호가 나온다.

![](https://raw.githubusercontent.com/arrow-economist/imageslibrary/main/SCR-20240407-ummp.png)

### LaTeX에서 숫자에 blackboard-bold (mathbb) 쓰는 방법

이 경우 해결 방법은 간단하다. 보통 `\mathbb`를 쓰기 위해선 `\amsmath` 패키지를 쓰게 되는데, 이 패키지 대신 `\bbm`이라는 패키지를 쓰고 `\mathbbm{1}`과 같이 써주면 된다.

```latex
\documentclass{article}
\usepackage{bbm}
\begin{document}
\[
\mathbbm{1}
\]
\end{document}
```

와 같이 입력을 해주면

![](https://i.stack.imgur.com/LOlzT.png)

올바르게 입력된 모습을 확인할 수 있다.
