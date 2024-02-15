---
title: obsidian Git 플러그인 사용 시 Fatal could not read username 에러
author: arrow
date: 2023-09-25 15:38:00 +0800
categories: [obsidian]
tags: [obsidian, git]
---

# #Obsidian #Github

요즘 열심히 쓰고있는 Obsidian. Github와 연동을 해주는 플러그인 Obsidian git에 대해 전에 포스팅도 했었다. [이 링크 참조](https://arrow-economist.github.io/ob/github/Obsidian-Obsidian-Github-%EC%97%B0%EB%8F%99/)

하지만 계속 쓰는데 어느 순간부터 문제가 발생했다. 갑자기

```
Fatal: Could not read Username for "https://github.com", No such device or address
```

이런 메시지가 자꾸 옵시디언에 떴다. 이유를 곰곰이 생각해보니 깃을 푸시하다가 personal token을 쓰라는 메시지를 보고 그걸 발급받고 나서부터 뭔가 제대로 연동이 안되었나보다. 그래서 commit까지는 되어도 push는 꼭 터미널로 해줘야했는데 상당히 귀찮았다.

그래서 열심히 뒤지다가 깃허브 공식 홈페이지에서 해결방법을 찾았다. [여기](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens)

# 해결방법

해결방법은 의외로 간단했다. personal token을 발급받고 HTTPS 상에 이걸 사용해줘야 하는데(?) (뭔말인지 나도 모릅니다)

```bash
git clone https://github.com/USERNAME/REPO.git
```

이걸 입력해주면 된다. 여기에 `USERNAME`은 내 깃허브 네임, `REPO`는 내 깃허브와 옵시디언을 연동해주는 repository 이름이다. 이걸 터미널에 입력하고 실행하면 username과 password를 입력하라는 창이 차례로 뜨게 된다. 이 때 password는 저장해둔 personal token을 입력하면 clone이 되고 이제 옵시디언에서 더이상 에러가 뜨지 않게 된다!

![enter image description here](https://raw.githubusercontent.com/arrow-economist/imageslibrary/main/SCR-20230924-uptq.png)

git에 대해 더 찬찬히 알아가야겠다.

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTQ2MTMxNDI3NywxMjg4NjA0ODQsLTM0NT
IyMzg5OF19
-->
