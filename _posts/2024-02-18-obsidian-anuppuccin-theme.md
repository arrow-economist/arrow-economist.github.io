---
title: 옵시디언 anuppuccin(아누푸친) 테마 적용 방법
author: arrow
date: 2024-02-18 00:34:00 +0800
categories: [obsidian]
tags: [obsidian]
---

# #obsidian #anuppuccin

옵시디언에 점점 예쁜 테마가 많아지는게 기분이 좋다. 그 중에 오늘은 **anuppuccin(아누푸친)** 테마를 적용하는 방법을 알아보도록 하겠다.

## 1. 아누푸친 테마 다운로드 받기

우선 `settings(톱니바퀴 모양) > Appearance > Themes`에서 `Manage`버튼을 누른다. 그러면 능력자 분들이 만들어놓은 옵시디언 테마를 검색할 수 있는데 여기에서 `anuppuccin`을 검색한다. 사실 `anu`만 검색해도 뜬다.

![](https://raw.githubusercontent.com/arrow-economist/imageslibrary/main/SCR-20240218-bngv.png)

아누푸친을 누르고 `install and use` 버튼을 누르면 설치는 완료된다.

한 가지 더 다운로드 받을 게 있다. `settings > Community plugins > Community plugins`에서 `Browse`를 눌러서 `Style Settings`를 다운로드 해준다. 이미 다운로드를 받은 사람이라면 물론 해당되는 부분은 아니다.

그리고 여기에서 추가적으로 해주면 좋은 부분이 있는데, [이 링크](https://github.com/AnubisNekhet/AnuPpuccin/blob/main/snippets/extended-colorschemes.css)를 들어가면 `AnuPpucin/snippets/extended-colorschemes.css`라는 파일이 보인다. 이 코드를 `Copy raw file`을 해주자.

그 뒤에 나의 옵시디언 Vault 폴더에 들어가서 `.obsidian`이라는 폴더를 들어가준다. 숨김폴더이므로 맥 기준으로는 `cmd+shift+.`을 누르면 숨김폴더를 볼 수 있다. 들어가면 `snippets`라는 폴더가 있는 경우(이전에 스니펫을 사용했다면 있다)는 이 폴더에 들어가면 되고 없다면 `snippets`라는 폴더를 만들어주면 된다. 여기에서 css파일을 만들어줘야하기 때문에, 나의 경우는 `snippets`폺더를 우클릭 한 뒤 `services > New Terminal at Folder`를 클릭해줬다. 터미널을 이 경로에서 열면 된다는 뜻이다.

터미널에

```zsh
code extended-color.css
```

를 입력해준다. 파일명은 크게 상관이 없는 것 같다. 실행하면 빈 vscode창이 뜨게 된다. (VScode가 없다면 `vi extended-color.css`를 쳐도 되지만, vim이 vscode보다 불편하기 때문에 vscode를 설치한 뒤에 이를 실행해주는 것을 추천한다.)

이 빈 파일에 아까 우리가 복사했던 그 raw file `AnuPpucin/snippets/extended-colorschemes.css`을 붙여넣기 해주고 저장을 한다. 그러면 드디어 준비 완료.

## 2. 입맛대로 테마 조정하기

옵시디언에서 style settings 플러그인이 enabled 되어있는지를 우선 확인하고, 되어있다면 `Settings > Appearance`에서 맨 밑에 CSS snippets라고 해서 아까 만들어줬던 `color-extended`가 있는 것을 확인할 수 있다. 이걸 클릭해서 enabled로 해주자. 혹시 맨 밑에 이게 안보인다면 `Community plugins`에서 `css snippets`를 검색해서 설치, 활성화해주면 보일 것이다.

밑의 `Community plugins`에 `style settings`를 들어가면 `AnuPpucin`과 `AnuPpuccin Themes Extende`가 보일텐데, 여기에서 후자를 클릭한다. 그러면 세 개의 토글 버튼과 테마 flavor가 보이는데, 버튼은 전부 활성화 해주고 flavor는 말 그대로 자기 입맛에 맞게 설정해주면 된다.

![](https://raw.githubusercontent.com/arrow-economist/imageslibrary/main/SCR-20240218-btcn.png)

나는 위와 같이 설정을 해주었다.

이제는 전자로 넘어가면 되는데, `Colors`는 우리가 이미 설정해줬으므로 넘어가면 된다. 이번엔 `File Editor & Markdown Elements`를 수정해보겠다. 여기에서 `Active line highlight`를 켜주고 `Checkboxes`에 있는 두 토글버튼을 전부 활성화를 해주면 예쁜 것들을 쓸 수 있는데, 어떤 것들이 가능한지는 [공식 문서 링크](https://github.com/AnubisNekhet/AnuPpuccin?tab=readme-ov-file#custom-checkboxes--speech-bubbles)를 참고하면 된다.

다른 부분 (`Codeblock`이나 `Typography` 등등)은 필요에 맞게 바꾸면 되는데, 나도 이것 저것 바꿔가면서 확인하고 예쁘게 꾸미는 중이다.

이 테마의 핵심이라고도 할 수 있는 부분은 밑의 `Workspace` 부분인데, 여기에서 `Colorful Frame`에 들어가서 `Enable Colorful Frame (WIP)`을 활성화해주면 위의 프레임 색을 조정할 수 있다.

다음의 `File Browser`에 들어가면 파일 아이콘, floating vault title, folder icons for collapse indicators등을 설정해줄 수 있는데, 나는 맨 위의 custom vault title을 빼고 활성화를 다 해주었다. 거기에 더해 `Rainbow Folders`에 들어가서 `Rainbow style`을 `simple`로 바꿔주고, `Simple Folder Settings`에 들어가서 전부 토글을 활성화해주면

![](https://raw.githubusercontent.com/arrow-economist/imageslibrary/main/SCR-20240218-bxkj.png)

이런 식으로 사이드 바도 예쁘게 꾸밀 수가 있다. ~~보니까 상단바가 마음에 안드는데 이 색깔은 나중에 조정해봐야겠다~~

그리고 `Tabs`에 들어가서 `Tab style`을 `Safari-style`로 바꿔주면 사파리 탭처럼 바꿀 수도 있다.

남은 부분은 하나씩 자기 입맛에 맞게 조정하면 될 것 같다. 이렇게 꾸미면 노션보다 예쁘고 노션보다 가볍고 노션보다 좋은 옵시디언 완성이다! ~~(옵시디언 홍보대사)~~
