---
title: jekyll-chirpy-theme으로-깃허브-블로그-만들기
author: author-id
date: 2024-02-14 22:22:00 +0800
categories: [git, github]
tags: [git, github]
---

# #github #깃허브블로그 #chirpy

블로그를 이사했다. 이사라고 하긴 뭐하지만, 테마를 바꿔봤다. 기존에 쓰던 minimal-mistakes는 구글링할게 많아서 처음에 접하긴 좋았지만 더 예쁜걸 찾아 떠났다. 그리고 내가 찾은게 **chirpy theme**.

[chirpy-theme](https://github.com/cotes2020/jekyll-theme-chirpy) << 공식 깃허브는 여기에서 확인할 수 있다.

이거를 하기 위해서 엄청 헤매고 헤매서 성공했기 때문에 기록을 남겨놓고, 또 내가 접한 에러를 해결하는 방법도 적어놓으려고 한다.

필자는 m2기반의 mac에서 만들었기 때문에, 윈도우나 리눅스 환경은 다소 다를 수 있다는 점을 참고 바란다.

# 깃허브 블로그 만들기

나는 git, github는 진짜 무지해서 그냥 깃허브에서 fork 시킨 뒤에 깃허브 사이트 내에서 블로그를 꾸며왔었다. (이전에 minimal-mistakes로 했을 때) 그런데 이 chirpy 테마는 그렇게 하기가 어려워서 어쩔 수 없이 깃을 배우고 여러가지를 깔면서 이것저것 부딪혀야만 했다... 그래서 이 포스트는 나처럼 아무것도 몰라도 블로그를 만들 수 있게끔 친절하게 써보려고 한다.

## 0. 다운로드 받아야 할 것들. (환경 구축)

우선 jekyll과 ruby를 써야하기 때문에 이것들을 다운로드 해줘야 한다. 다음의 명령어를 터미널을 켜서 복붙 후 실행해주자.

```zsh
brew install ruby
```

만약 `brew`도 안깔려있다면,

```zsh
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

이걸 그대로 복붙해서 실행하면 brew가 설치되고, brew를 설치 후 위 명령어를 다시 실행하면 된다.
([참고: homebrew](https://brew.sh))

그리고, 방금 위에 링크를 올린 [chirpy-theme](https://github.com/cotes2020/jekyll-theme-chirpy) 여기에서 Fork를 눌러서 본인의 깃허브 repo를 만들도록 하자. 이 때 repo 이름은 `username.github.io`이렇게 입력해주면 된다. 나의 경우는 `arrow-economist.github.io`가 되겠다.

제대로 fork를 했으면 이제 이거를 내 컴퓨터 local에 불러오는 작업을 해야한다. 만약 git이 처음이라면? 그 때는 최초 설정을 해줄 필요가 있는데 (맥은 git이 기본으로 설치되어있는 것으로 알고있음)

```
git config --global user.name "깃허브아이디"
git config --global user.email "이메일"
```

아마 이걸 처음 세팅하는 사람이라면 git이 두 개 이상이 아니고, 그리고 맞더라도 나보단 잘할테니 그 부분은 생략하겠다. 여기에서 `"깃허브아이디"`는 나의 경우 `arrow-economist`에 해당하는 부분이고, `이메일`은 깃허브를 가입할 때 쓴 이메일을 그대로 입력해줬다. 두 명령어를 하나씩 차례대로 실행하면 된다.

## 1. git clone

```
git clone https://github.com/arrow-economist/arrow-economist.github.io
```

그리고 위 명령어를 이제 실행해주면 된다. 여기에서 `arrow-economist`에 해당하는 부분은 전부 본인의 `깃허브 아이디`로 바꾸면 된다.

```
git clone git@github.com-arrow-economist:arrow-economist/arrow-economist.github.io.git
```

참고로 나는 내 맥에 깃 아이디가 2개라서 이 명령어를 실행해서 클론을 해줬다. 사실 정확히 어떻게 다른지 이런걸 설명할만큼 잘 아는게 아니라서 이 부분은 두 명령어 중 본인에게 해당되는 것으로 실행하면 된다.

## 2. chirpy 초기화 진행

사실 이 부분이 제일 중요한 것 같다. 나는 이 부분에서 막혀서 한참을 헤맸다. 다음의 명령어를 `username.github.io` 폴더에서 실행해야 한다. 무슨 말인지 잘 모르겠다면, 맥에서 `username.github.io`가 있는 경로로 간다. 해당 폴더에서 우클릭 후 맨 밑에 `services`를 클릭 후 `New terminal at Folder`를 누르면 된다.

```bash
bash tools/init
```

많은 블로그와 [공식 가이드](https://chirpy.cotes.page/posts/getting-started/)를 살펴봐도 `bash tools/init.sh`라고 나와있거나 조금씩 달랐는데, 이를 실행해도 제대로 되지 않았다. 별로 중요한 부분이 아닌가보다 하고 넘겼는데 그 차이로 에러가 계속 발생했던 것 같다. 현재 포스팅 날짜 (2024년 2월) 기준으로는 위의 명령어가 맞다. 이걸 실행해주면 chirpy 테마가 초기화가 된다. 만약 에러가 난다면 `Node.js`때문일 확률이 있으므로

```
brew install node
```

나 다른 명령어를 통해 해결해보도록 한다. [참고 사이트](https://nodejs.org/en/download/package-manager)

## 3. 확인 절차

이제 거의 다 되었다.

```
bundle
```

이 명령어를 역시 clone 된 폴더 경로에서 실행하면 된다. 뭐가 깔리는 모습들이 보이는데, 잘 설치가 되었다면 다음엔

```
bundle lock --add-platform x86_64-linux
```

이 명령어를 실행해주면 된다. 이 명령어는 리눅스 기반이 아닌 OS에서 구동이 되게끔 해주는 것이라고 들었다.

```
jekyll serve
```

명령어를 실행했을 경우
![](https://raw.githubusercontent.com/arrow-economist/imageslibrary/main/SCR-20240214-twew.png)

이와 같이 https://127.0.0.1:4000/이라는 서버 주소가 뜨게 된다. 내 로컬 주소인데 이걸 실행해서 [이 페이지](https://chirpy.cotes.page)와 같은 화면이 뜬다면 성공한 것이다.
이 명령어를 종료하고 싶으면 `ctrl c`를 입력해서 꺼주면 된다. (`cmd c`가 아니다.)

## 4. 나의 블로그로 다듬어가기

이제 담겨있는 파일들을 수정해가면서 내 블로그로 만들어가면 되는데 이 부분은 다음 포스팅에서 계속 하도록 하겠다.

참고로 3단계까지 성공했을 경우, git 상에서 push를 해준게 없기 때문에 주소창에 입력해도 실행이 되지 않는게 정상이다. 다음 포스팅까지 거쳐서 블로그를 완성할 수 있다.

## 5. 생길 수 있는 에러

내가 직면했고 가장 날 괴롭혔던 에러는

```
--- layout: home # Index page ---
```

아무리 어떻게 해봐도 arrow-economist.github.io로 들어갔을 때, 위와 같은 문구만 뜨는 경우였다. 열심히 검색해본 결과 몇 가지의 해결 방법이 있었는데,

1. `bundle lock --add-platform x86_64-linux` 이 명령어를 제대로 실행하지 않았을 경우 다시 실행해보기
2. github 상의 내 repo >> settings >> pages >> build and deployment에서 source를 github actions로 바꾸기

이 정도였는데 두 경우를 다 실행해봐도 에러는 계속되었다. 하지만 나는 앞서 말했던 제일 중요한 부분인 초기화 부분에서 답을 찾았다.

3. `bash tools/init` 이 명령어를 실행을 꼭 해주자. 그래야 세팅이 되면서 구동이 가능한 것 같다. 혹시 나와 비슷한 문제로 계속 블로그가 안열린 사람이라면 이 명령어로 해결이 되길 바란다.
