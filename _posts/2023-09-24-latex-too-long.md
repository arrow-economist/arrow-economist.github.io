---
title: LaTeX 수식이 너무 길 때
author: arrow
date: 2023-09-24 00:38:00 +0800
categories: [latex]
tags: [latex]
---

# #LaTeX

LaTeX로 수식을 쓰다보면, 수식이 너무 길어질 때가 있다. 그러면 페이지에서 잘리고 여러가지로 골치가 아파지는데 그 때 해결을 하려고 구글링을 해봤는데 `\allowbreak`이런거를 쓰면 된다고 했다. 그렇지만 이런걸로 해결이 안됐는데 그 이유는 바로 내 수식에 `\left[` `\right]`과 같이 괄호를 크게 만들기 위해 쓰는 `\left` `\right`가 있기 때문이었다.

예를들어

```
$$
\frac{1}{n^2h_1^2h_2^2} \left\{ \int\int f(x_1)f(x_2)k^2\left( \frac{X_{1i}-x_1}{h_1}\right)  k^2 \left( \frac{X_{2i}-x_2}{h_2} \right)dx_2dx_1 - \left[\int\int f(x_1)f(x_2)k\left( \frac{X_{1i}-x_1}{h_1}\right)  k \left( \frac{X_{2i}-x_2}{h_2} \right)dx_2dx_1 \right]^2 \right\}\\
$$
```

와 같은 수식을 쓰려고 한다면 수식이 길어져 compile을 했을 때 결과물이 짤리므로 줄을 한칸 띄워야한다.

![enter image description here](https://raw.githubusercontent.com/arrow-economist/imageslibrary/main/SCR-20230924-rulr.png)

하지만 `\\`로 줄을 띄우면 `\left` `\right`가 한 줄에 있지 않아서 코드에러가 발생한다. 해결 방법은 생각보다 간단했다.

우선 `\left` `\right`를 안쓰면 된다. 그러면 괄호가 작아지는데 그 대신 우리는 `\biggl` `\biggr`을 쓰면 된다. 역할은 `\left` `\right`와 동일한데 크기가 큰 상태로 fixed되어있는 명령어다.

```
$$
&= \frac{1}{n^2h_1^2h_2^2} \biggl\{ \int\int f(x_1)f(x_2)k^2\left( \frac{X_{1i}-x_1}{h_1}\right)  k^2 \left( \frac{X_{2i}-x_2}{h_2} \right)dx_2dx_1 \\
&\qquad - \left[\int\int f(x_1)f(x_2)k\left( \frac{X_{1i}-x_1}{h_1}\right)  k \left( \frac{X_{2i}-x_2}{h_2} \right)dx_2dx_1 \right]^2 \biggr\}\\
$$
```

![수식을 완성한 모습](https://raw.githubusercontent.com/arrow-economist/imageslibrary/main/SCR-20230924-rtgm.png)
처럼 쓴다면 두 줄로 한 수식을 나눠서 쓸 수 있다. `&=`과 `&\qquad -`등으로 수식 정렬을 하면 깔끔하게 쓸 수 있고 한 수식이 끝나지 않았음을 `&\qquad`로 들여쓰기 해서 표현할 수 있다!

Stackedit상에서 수식이 자꾸 표현이 안되어서 사진으로 대체했다.

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE2NjU3MjM1MDddfQ==
-->
