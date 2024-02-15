---
title: latex-수식-번호-관련-팁
author: arrow-economist
date: 2024-02-11 00:38:00 +0800
categories: [latex]
tags: [latex]
---

# #LaTeX

우선 기본적으로 나는 레이텍에서 수식을 입력할 때 `\begin{align} \end{align}`을 쓴다. eqnarray도 있는데 이유는 모르겠고 그냥 `align`이 더 좋았던 것 같다. 그리고 여기에 `*`을 붙여서 `\{align*}`을 하면 번호가 매겨지지 않은 수식을 입력할 수 있다.

### 여러 수식 중 몇 개는 번호를 매기지 않고 싶을 때

그런데 예를 들어서 두 줄의 수식을 입력하는데, 한 줄의 수식에는 번호가 필요가 없다면 어떻게 해야할까? 바로 `\nonumber`를 활용하면 된다.

```
\begin{align}
    \alpha_i &= \alpha + \pi_{1_y} \ln y_i + \sigma_1 v_i^1\\
    \beta_i &= \beta + \pi_{2_y} \ln y_i + \sigma_2 v_i^2 \nonumber
\end{align}
```

이렇게 입력하면

![enter image description here](https://raw.githubusercontent.com/arrow-economist/imageslibrary/main/SCR-20240211-djdo.png)
이렇게 `\nonumber`를 입력한 식에는 번호가 들어가지 않은 것을 확인할 수 있다.

### 여러 수식을 하나의 번호로만 매기고 싶을 때

혹은 수식은 여러개인데 전체 수식에 하나의 넘버만을 부여하고 싶을 때는 어떻게 하면 될까? 그럴 때는 `\begin{split} \end{split}`을 사이에 넣어주면 된다.

```
\begin{align}
	\begin{split}
	    \alpha_i &= \alpha + \pi_{1_y} \ln y_i + \sigma_1 v_i^1\\
	    \beta_i &= \beta + \pi_{2_y} \ln y_i + \sigma_2 v_i^2
    \end{split}
\end{align}
```

이렇게 입력하면

![enter image description here](https://raw.githubusercontent.com/arrow-economist/imageslibrary/main/SCR-20240211-dkpg.png)
이렇게 수식의 가운데에 번호가 매겨지는 것을 확인할 수 있다.

<!--stackedit_data:
eyJoaXN0b3J5IjpbNjIzODc2NjQ5XX0=
-->
