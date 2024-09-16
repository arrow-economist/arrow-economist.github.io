---
title: 논문쓸 때 git 협업에 활용하기
author: arrow
date: 2024-09-15 22:00:00 +0800
categories: [git, github]
tags: [git, github]
---

# #Git #Github
교수님과 논문을 같이 쓰게 되면서 버전 관리의 필요성을 느끼게 되었다. 드롭박스로도 가능하긴 하지만, fancy하고 더 안정적인 방법을 써보고자 git을 활용하게 되었다. 깃에 대해 잘 모르지만 내가 보기 위해 정리를 해보고자 한다.

## 1. 깃 세팅
### 1. repo 만들기
우선 깃허브에 들어가서 repository를 하나 만들어준다.

![](https://raw.githubusercontent.com/arrow-economist/imageslibrary/main/SCR-20240915-tlut.png)

repository name은 공백 없이 간결하게 만들면 좋다. 그리고 "-"를 이용해서 공백을 대신할 수 있다. Public으로 하면 내 Work in Progress 논문이 다 까발려지기 때문에 Private으로 나는 선택했다.

### 2. Repository를 로컬에 Clone하기
코드 버튼을 누르면 내 repository 주소를 복사할 수 있다. 이걸 복사해둔다.  
내가 앞으로 이 Repo를 관리할 **내 컴퓨터 상의 폴더**에서 터미널을 켜준다.  
그리고 다음의 코드를 실행해준다.

```bash
git clone https://github.com/yourusername/repositoryname.git
```
여기에서 `yourusername`에는 깃허브 유저네임을, `respositoryname`에는 깃허브 repo 이름을 적어주면 된다.

## 2. 협업하기

### 1. Branch 만들기
쉽게 말해 브랜치를 만들게 되면, 최종 파일을 건드리지 않고 새로운 버전을 만들어서 내 마음대로 수정이 가능하다. Git 브랜치의 구조 등은 다른 블로그에서 더 자세하게 설명해 놓은게 많기 때문에 그건 생략하도록 한다. 그냥 직관적으로, 하위 브랜치에서 만든 파일을 깃허브에 올려서 이 수정본에 대해 논의를 거친 후에 최종본에 업로드를 하는 형식이라고 생각하면 된다.

``` bash
git checkout -b aa
```
혹은

``` bash
git branch aa
git checkout aa
```
이런 식으로 `aa`라는 브랜치를 만들어서 `aa`로 전환을 해주면 된다. (`checkout`이 전환하는 명령어라고 이해하면 된다.)

### 2. 파일 수정하기
이렇게 브랜치를 만들고 나서 내가 원하는 대로 페이퍼를 수정해주면 된다. 이 때 내가 수정하는 파일 명을 `paper.tex`라고 하겠다.

### 3. 수정된 부분을 stage하기
``` bash
git add paper.tex
```
다음과 같이 `add`를 하게 되면 현재 내 브랜치 상에서 수정된 부분을 commit하기 전에 stage하는 것이다. 무슨 말인지 잘 모르겠으니 그냥 말 그대로 깃허브 서버에 바뀐 것을 `add`한다고 생각해보자.
혹은 파일 여러개가 변화했다면,
``` bash
git add .
```
이렇게 `.`을 쓰면 전체를 `add`하겠다는 뜻이다.

### 4. 수정된 부분을 commit하기
이제 메시지와 함께 커밋이라는 것을 진행할 수 있다.
``` bash
git commit -m "0910 revised the introduction"
```
이런 식으로 `git commit -m` 명령어 다음에 큰따옴표와 함께 작은 메모를 해두면, 깃허브 상에서 내가 어떤 것을 변화시켰는지 메시지를 통해 한 눈에 확인할 수 있게 된다.

### 5. push 하기
마지막으로는 push라는 것을 진행하면 되는데,
``` bash
git push origin aa
```
이렇게 내 `aa` 브랜치를 깃허브에 푸시하게 된다.

## 3. 수정본 검토 후 최종본 변경하기

여기에서는 git 명령어를 통해서 하는 방법도 있지만, github webpage를 이용하는 방법으로 설명해보겠다.

### 1. Pull request 만들기
협업을 잘 하면 각자 브랜치에서 push한 변경본들이 github의 내 repository에 올라와있을 것이고, create a pull request라는 버튼이 보일 것이다.  

누르면 바로 pull request를 할 수 있는데 이제는 merge를 할 단계이다.

### 2. merge하기

쉽게 말해 수정본을 최종본에 합친다는 뜻이라고 보면 된다. 토론을 거친 후 특이사항이 없다면 merge를 하면 된다.

### 3. pull하기
깃허브 웹페이지에 최종본이 형성되었기 때문에, 이걸 다시 내 컴퓨터의 폴더 상에 업데이트를 해줘야하는데, 그 과정이 pull이라고 생각하면 된다.

``` bash
git checkout main
git pull origin main
```
`main`으로 브랜치를 다시 바꿔주고, `pull`을 진행하면 된다.

마지막으로는

``` bash
git branch -d aa
```
생성했던 브랜치를 삭제해주면 끝이 난다.
  
  
혹시 잘못된 부분이 있다면 댓글을 남겨주면 바로 수정하도록 하겠다. 나도 깃을 잘 몰라서 여전히 배우는 중이다.