---
title: jekyll chirpy theme에 댓글 기능 추가하기 feat. utterances
author: arrow
date: 2024-02-19 12:16:00 +0800
categories: [git, github]
tags: [git, github]
---

# #github #utterances

저번 포스팅을 통해서 chirpy theme으로 깃허브 블로그를 만들어보았다.

링크: [chirpy theme으로 깃허브블로그 만들기](https://arrow-economist.github.io/posts/chirpy-theme/)

나는 원래 disqus로 댓글 기능을 쓰고 있었는데, 디스커스보다 utterances가 요즘 더 대중적이고 많이 쓰이는 것 같아서 이걸로 바꿔보려고 한다.

## 1. utterances 연결하기

[이 링크](https://github.com/apps/utterances)를 통해서 우선 내 깃허브에 utterances를 설치&연결해주면 된다. 그러면 어떤 repository에 연결할지도 고를 수 있는데, 일단은 내 깃허브 블로그 repo만 연결을 해보겠다. 그 때는 `arrow-economist/arrow-economist.github.io` 이런 식으로 써주면 된다.

`Blog Post ↔️ Issue Mapping` 쪽은 정확히 뭐가 다른지 잘 모르겠지만 대체로 사람들이 `Issue title contains page pathname`을 고르길래 이걸 따라서 했다. `Theme`도 내 테마에 맞게 잘 고르면 `Enable Utterances`에 무슨 코드가 뜨게 된다.

## 2. \_config.yml에 추가하기

하지만 나는 jekyll chirpy theme를 사용 중이기 때문에 저 코드를 복사 붙여넣기 하지 않아도 된다. 우선 내 테마에서 `_config.yml` 파일을 들어간다. 그러면 대략 88행부터 이런 코드가 보인다.

```yml
comments:
  active: "utterances" # The global switch for posts comments, e.g., 'disqus'.  Keep it empty means disable
  # The active options are as follows:
  disqus:
    shortname: arroweconomist # fill with the Disqus shortname. › https://help.disqus.com/en/articles/1717111-what-s-a-shortname
  # utterances settings › https://utteranc.es/
  utterances:
    repo: arrow-economist/arrow-economist.github.io # <gh-username>/<repo>
    issue_term: # < url | pathname | title | ...>
  # Giscus options › https://giscus.app
```

여기에 `active`에 `"utterances`를 써주고, `utterances: repo:`에는 `깃허브아이디/깃허브아이디.github.io`를 써주면 된다. 저장하고 `git push`까지 진행시키면 댓글 기능이 자동으로 활성화 되는 것을 확인할 수 있다.

## 3. 댓글 기능이 안된다면?

나는 댓글기능이 열려있길래 달리는게 될 줄 알았는데 테스트를 해봤더니 댓글이 안달렸다. 왜 그럴까 하고 열심히 검색해봤는데, 의외로 해결 방법은 간단했다.
우선

깃허브에 들어가서 `깃허브아이디.github.io` repo의 `settings`를 들어간다. 그러면 `General` 탭에서 밑에 좀 내렸을 때 `Features`에서 `Issues`가 체크가 활성화되어있는지를 확인해보도록 한다. 이게 활성화가 안되어있으면 댓글 기능을 쓸 수가 없다. 만약 이게 체크가 되어있는데 안된다면, `_config.yml`에서 `url`을 맞게 입력했거나, utterances의 `path`를 맞게 입력했는지 확인해보자!

댓글 기능을 쓸 수 있는지 확인하려면 밑에 한 번... 살포시 댓글을 남겨보도록 한다.🫶
