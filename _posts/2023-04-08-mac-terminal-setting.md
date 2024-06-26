---
title: 맥 터미널 세팅하는 방법
author: arrow
date: 2023-04-08 00:34:00 +0800
categories: [Mac]
tags: [Mac]
---

# #MacOS #Terminal

필자는 컴못알이라 원래 윈도우 노트북만 썼다. 그러다가 석사 입학 후 코딩을 많이 하게 되었는데, M1 맥북이 나왔을 때 속도가 쩐다는 소식을 듣고 작업 환경 개선을 명목으로 질러버렸다. 대만족 후 애플에 빠져들어 지금은 맥미니까지 쓰고 있다. 하지만 여전히 컴못알이다. 얼마 전에 맥북 세팅을 검색해보다가 터미널을 세팅하는 방법을 찾게 돼서 공유를 해본다. 물론 나는 터미널을 세팅해놓고도 쓸 줄 모르는 사람이다. (참고: 노마드 코더 유튜브)

### 1. Homebrew 설치

우선 [brew.sh](https://brew.sh)에 접속한다. 그러면 다음과 같은 화면이 나오는데, 여기에서 **Install Homebrew**에 있는 코드를 복사해준다.

![enter image description here](https://raw.githubusercontent.com/arrow-economist/arrow-economist.github.io/master/images/Terminal1.png)

복사한 커맨드를 터미널에 붙여넣기 하고 실행을 하면 된다. (터미널은 **cmd + space**로 Spotlight를 켜서 실행하면 된다.) 그러면 맥 비밀번호를 입력하라는 창이 뜨는데, 비밀번호를 입력 후 엔터를 눌러준다. 그러면 뭔가가 설치되는 듯한 느낌이 들고, 맨 마지막에 이런 안내문구가 뜬다.

```ruby
==> Next steps:
- Run these two commands in your terminal to add Homebrew to your PATH:
    echo 'eval "$(/opt/homebrew/bin/brew shellenv)"! >> /Users/~~ file
    eval "$ (/opt/homebrew/bin/brew shellenv)"
```

이 문구는 자신의 맥에 따라 약간 다르므로 자기의 터미널에 뜬 커맨드를 순서대로 복사 붙여넣기를 하여 실행해준다. 완료되었다면, 터미널을 완전 종료 후 다시 열면 첫 번째 단계 끝!

### 2. iterm2 설치하기

다음으로는 기존의 터미널을 대체할 iterm2를 설치해야 한다. 방금 설치했던 homebrew를 이용해서 설치를 할 예정이다. 터미널에 밑의 명령어를 실행해준다.

```bash
brew install --cask iterm2
```

homebrew를 잘 설치했다면 아마 설치가 되는 듯한 인터페이스가 뜰 것이다. 에러없이 설치가 끝났다면 두 번째 스텝도 완료!

### 3. Oh my zsh 설치하기

다음으로는 Oh my zsh를 설치해서 터미널 UI를 간지나게 꾸며줄 차례다. [ohmyz.sh](https://ohmyz.sh)를 들어가면, **Install oh-my-zsh** 버튼이 보인다. 누르면 하단으로 내려가서 설치를 할 수 있는 코드가 나와있는데 이를 복사해준다.

![enter image description here](https://raw.githubusercontent.com/arrow-economist/arrow-economist.github.io/master/images/Terminal2.png)

iterm2에 붙여넣기 후 실행을 하면 예쁜 Oh My Zsh 도트문구가 보이는 것을 확인할 수 있다. 그리고 [powerlevel10k](https://github.com/romkatv/powerlevel10k)로 들어가보자. 밑의 *Readme*에서 Installation을 클릭 후 **Oh my zsh**를 클릭하면

```bash
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```

이런 코드가 있는데, 이걸 복사 후 아까 Oh My Zsh를 깔았던 iterm2에 들어가서 실행을 시켜준다. 그리고 터미널 환경파일을 열어야한다. **Visual Studio Code**기준으로는

```bash
code ~/.zshrc
```

이렇게 터미널에 입력 후 실행하면 VSCode에서 환경파일이 열린다. 하지만 여기서 간혹 터미널에서

> zsh: command not found: code

와 같은 에러가 뜨는 경우가 있다. 이럴 때는 터미널에 다음과 같은 명령어를 입력해보자.

```bash
ln -s "/Applications/Visual Studio Code.app/Contents/Resources/app/bin/code" /usr/local/bin/code
```

이랬는데 만약 이미 code가 존재한다고 하는 경우도 있다. 그 경우는, VSCode에 들어가서 **cmd+shift+p**를 누르고

> **Shell Command: Uninstall 'code' command from PATH**

이걸 입력 후 실행해준 뒤, 여기에 Uninstall을 **install**로 바꾼 명령어를 한 번 더 실행해준다. 그러고 터미널에 가서 환경파일을 여는 코드를 실행하면 VSCode로 정상적으로 열 수 있다.

VSCode가 열리면 다음과 같은 코드가 첫째 줄부터 보인다.

```bash
# Enable Powerlevel10k instant prompt. Should stay close to the top of ~/.zshrc.
# Initialization code that may require console input (password prompts, [y/n]
# confirmations, etc.) must go above this block; everything else may go below.
if [[ -r "${XDG_CACHE_HOME:-$HOME/.cache}/p10k-instant-prompt-${(%):-%n}.zsh" ]]; then
 source  "${XDG_CACHE_HOME:-$HOME/.cache}/p10k-instant-prompt-${(%):-%n}.zsh"
fi

# If you come from bash you might have to change your $PATH.
# export PATH=$HOME/bin:/usr/local/bin:$PATH

# Path to your oh-my-zsh installation.
export  ZSH="$HOME/.oh-my-zsh"

# Set name of the theme to load --- if set to "random", it will
# load a random theme each time oh-my-zsh is loaded, in which case,
# to know which specific one was loaded, run: echo $RANDOM_THEME
# See https://github.com/ohmyzsh/ohmyzsh/wiki/Themes
ZSH_THEME="robbyrussell"
```

여기에서 `ZSH_THEME="robbyrussell"` 부분을 `ZSH_THEME="powerlevel10k/powerlevel10k"` 이렇게 바꿔주고 저장 후 종료를 하면 된다. 터미널도 종료를 하자.

### 4. iterm2 커스텀하기

지금까지 잘 따라왔다면 iterm2를 재시작했을 때 평소와는 다른 화면이 떠야 한다. Powerlevel10k configuration wizard (환경설정 마법사)가 뜨면 성공한거다. 폰트를 설치하기 위해 (_y_)를 눌러준다. 설치가 끝나면 종료 후 재시작을 한다.

재시작을 하면 다이아몬드 아이콘부터 몇 개의 아이콘들이 정상적으로 보이는 지를 물어보는 질문이 나온다. 보이는 대로 답을 해주면 그 다음부터는 Prompt style을 지정할 수 있다. 원하는 대로 입맛에 맞게 설정을 해준 후, 마지막에 **(1) Verbose (Recommended)**를 선택해주고, **(y) Yes (Recommended)**를 누르면 설정이 끝이 난다. 다시 재시작을 해보자!

![enter image description here](https://raw.githubusercontent.com/arrow-economist/arrow-economist.github.io/master/images/Terminal3.png)

[설정 예시1]

![enter image description here](https://raw.githubusercontent.com/arrow-economist/arrow-economist.github.io/master/images/Terminal4.png)

[설정 예시2]

이렇게 보니 나는 뭔가 깔끔한 걸 선호하는 것 같다. 마지막으로 몇가지 세팅을 더 해줄 계획이다. iterm2를 열고 Settings를 열어보자.(단축키: **cmd + ,**)

![enter image description here](https://raw.githubusercontent.com/arrow-economist/arrow-economist.github.io/master/images/Terminal5.png)

여기에서 **Theme**을 보면 여러가지가 있는데, **Minimal**를 누르면 상단바랑 터미널 창의 색이 통일되면서 미니멀한 느낌을 주는게 마음에 든다.

![enter image description here](https://raw.githubusercontent.com/arrow-economist/arrow-economist.github.io/master/images/Terminal6.png)

다음으로는 **Profiles**에서 **Text**를 보면, 폰트를 지정할 수 있다. 나는 여러가지를 해본 결과 *Courier New*가 가장 마음에 들어서 이걸로 해놨다. 한 번씩 글씨체를 바꿔주는 것도 코딩에 리프레시가 될 것 같다. 글씨 크기도 나는 조금 키웠고 자간, 행간을 1씩 키웠다.

![enter image description here](https://raw.githubusercontent.com/arrow-economist/arrow-economist.github.io/master/images/Terminal7.png)

마지막으로 상태창을 만들어줄건데, **Profiles**에서 **Session**을 보면, 맨 마지막에 *Status bar enabled*라는 칸이 있다. 이걸 체크해주고, **Configure Status Bar**를 누르면 상태바를 내 마음대로 조정할 수 있다. 마음에 드는 것들을 골라서 올려놓자. 그러면 이제 다꾸도 아니고 터꾸(터미널 꾸미기)가 완성이다.

![enter image description here](https://raw.githubusercontent.com/arrow-economist/arrow-economist.github.io/master/images/Terminal8.png)

이렇게 꾸미고 여기에 파이썬을 해야 간지인데, 아직 그정도는 못된다. 언젠간 터미널을 써먹는 날도 오겠지?

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTM2NDI4Njk0OSwtMTQzMzMyNzM1LC0xNT
M3Mzc3OTUyLC0yMTk3ODAyNDUsNTUxOTU3OTIsLTE0OTM4MTAx
MjYsMTUwNTI4NjU1Nl19
-->
