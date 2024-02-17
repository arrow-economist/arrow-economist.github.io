---
title: Julia 기본 터미널을 iterm2로 변경하는 방법
author: arrow
date: 2024-02-17 01:29:00 +0800
categories: [julia]
tags: [julia]
---

# #julia #mac #iterm2

맥에서 줄리아는 기본 terminal 앱으로 실행되게 되어있다. 그렇지만 이 default 설정을 iterm2로 바꾸고 싶을 때는 어떻게 해야할까?  
[참고링크](https://stackoverflow.com/questions/65147259/how-to-make-julia-app-launch-in-iterm-instead-of-macos-terminal-app)

## 줄리아 디폴트 터미널 변경하기

우선 `applications` 폴더에 들어가서 줄리아 아이콘을 오른쪽 클릭 해준다. 그리고 `show package contents`를 클릭해주면 줄리아 폴더를 들어갈 수 있다.
이 때`Contents/Resources/Scripts/main.scpt`를 실행해준다.

실행하면 4줄 정도의 스크립트 파일이 있는데, 이를 다음과 같이 변경해주면 된다.

```
set RootPath to (path to me)
set JuliaPath to POSIX path of ((RootPath as text) & "Contents:Resources:julia:bin:julia")
set JuliaFile to POSIX file JuliaPath
tell application "iTerm"
	tell current window
		create tab with default profile command "/Applications/Julia-1.9.app/Contents/Resources/julia/bin/julia"
		activate
	end tell
end tell
```

여기에서 `Julia-1.9.app`은 본인 버전에 맞는 숫자를 입력해주면 된다. 여기에서 저장을 하면 편집이 안된다고 에러가 뜰 수 있는데

![](https://raw.githubusercontent.com/arrow-economist/imageslibrary/main/SCR-20240217-cdkp.png)

이렇게 App management에서 script editor를 허가해주면 저장이 된다.

그리고 저장을 하고나면 줄리아를 실행할 때 이제 iterm2에서 실행이 된다.
