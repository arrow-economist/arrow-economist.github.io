---
title: LaTeX-표-꿀팁-(원하는-위치,-생성기)
author: arrow-economist
date: 2023-04-28 11:38:00 +0800
categories: [latex]
tags: [latex]
---

# #LaTeX #Table

레이텍을 쓰다가 표를 만들 일이 상당히 많다. 필자도 강의계획서를 만들다가 표를 만들려고 하는데 잊고 있었던 것들이 생각나서 기록하고자 포스팅을 한다.

### 1. 표 생성기

레이텍으로 표를 생성하는 것은 상당히 귀찮고 어렵다. 예전에는 이걸 일일이 만들었는데, 알고보니 생성을 도와주는 사이트가 따로 있더라. 바로 [여기](https://www.tablesgenerator.com/#)! Tablesgenerator라는 사이트로 LaTeX 외에도 html, markdown 등 다양한 언어를 지원한다.

![](https://raw.githubusercontent.com/arrow-economist/imageslibrary/main/LatexTable2.png)

들어가면 이런 모습이 나온다. 위의 테이블 형태에 내가 원하는대로 내용을 입력하고, 셀을 합치거나 나누고, 정렬을 조정하는 등의 행동을 하면 된다. 그리고 **Generate** 버튼을 누르면 밑의 코드가 내가 만든 테이블대로 바뀌게 된다.

![enter image description here](https://raw.githubusercontent.com/arrow-economist/imageslibrary/main/LatexTable1.png)

이렇게 만들고 확인을 누르면?

```latex
\begin{table}[]
\begin{tabular}{lllll}
\hline
\multicolumn{5}{c}{\textbf{Part 1: Introduction}}                                                      \\ \hline
\multicolumn{4}{l}{Introduction to Macroeconomics}                                        & Ch.1       \\
\multicolumn{4}{l}{The Measurement and Structure of the National Economy}                 & Ch.2       \\ \hline
\multicolumn{5}{|c|}{\textbf{Part 2: Long-Run Economic Performance}}                                   \\ \hline
\multicolumn{4}{l}{Productivity, Output, and Employment}                                  & Ch.3       \\
\multicolumn{4}{l}{Consumption, Saving, and Investment}                                   & Ch.4       \\
\multicolumn{4}{l}{The Asset Market, Money, and Prices}                                   & Ch.7       \\ \hline
\multicolumn{5}{|c|}{\textbf{Part 3: Business Cycles and Macroeconomic Policy}}                        \\ \hline
\multicolumn{4}{l}{The IS-LM/AD-AS Model: A General Framework for Macroeconomic Anaylsis} & Ch.9     \\ \hline
\end{tabular}
\end{table}
```

이렇게 LaTeX 코드를 만들어준다! 근데 표 라인을 만드는 건 좀 불편한 것 같아서, 이렇게 내가 만든 후에 Overleaf에서 직접 수정해주는 편이다.

### 2. 표를 원하는 위치에 넣기

보통 LaTeX에서 표를 생성하면 페이지의 최상단에 표를 넣게 된다. 하지만 나는 내 강의계획서에서 딱 내가 입력한 부분에 표를 삽입하고 싶다. 그럴땐 방금의 코드에서 하나만 추가해주면 된다. 바로 `\begin{table}[]`의 대괄호에 `hbt!`만 넣어주면 된다.

```latex
\begin{table}[hbt!]
\begin{tabular}{lllll}
\hline
\multicolumn{5}{c}{\textbf{Part 1: Introduction}}                                                      \\ \hline
\multicolumn{4}{l}{Introduction to Macroeconomics}                                        & Ch.1       \\
\multicolumn{4}{l}{The Measurement and Structure of the National Economy}                 & Ch.2       \\ \hline
\multicolumn{5}{c}{\textbf{Part 2: Long-Run Economic Performance}}                                   \\ \hline
\multicolumn{4}{l}{Productivity, Output, and Employment}                                  & Ch.3       \\
\multicolumn{4}{l}{Consumption, Saving, and Investment}                                   & Ch.4       \\
\multicolumn{4}{l}{The Asset Market, Money, and Prices}                                   & Ch.7       \\ \hline
\multicolumn{5}{c}{\textbf{Part 3: Business Cycles and Macroeconomic Policy}}                        \\ \hline
\multicolumn{4}{l}{The IS-LM/AD-AS Model: A General Framework for Macroeconomic Anaylsis} & Ch.9     \\ \hline
\end{tabular}
\end{table}
```

이렇게 하면, 내가 입력한 부분에서 최대한 위치를 변경하지 않고 표를 삽입해달란 뜻이 된다. 내가 원하는 부분에 표를 넣을 수 있게 되었다.

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTA1NDMyMjA5MV19
-->
