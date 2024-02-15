---
title: jekyll-chirpy-theme으로-깃허브-블로그-만들기-2
author: arrow
date: 2024-02-14 23:36:00 +0800
categories: [git, github]
tags: [git, github]
---

# #github #깃허브블로그 #chirpy

[jekyll chirpy theme으로 깃허브 블로그 만들기 part 1](https://arrow-economist.github.io)

이어서 가보도록 하겠다. 꼭 앞의 절차를 다 거치고 이 글을 읽기를 바란다.

# 4. 나의 블로그로 다듬어가기

이제는 내 로컬 폴더에서 `_config.yml`을 수정해줄 차례이다. 이 파일을 수정하면 큰 틀을 수정할 수 있다. 로컬폴더를 들어가 이 파일을 찾아 실행해주거나 vscode가 깔려있다면

```
code _config.yml
```

을 실행해주면 편집이 가능하다.

```yml
# The Site Configuration

# Import the theme
theme: jekyll-theme-chirpy

# The language of the webpage › http://www.lingoes.net/en/translator/langcode.htm
# If it has the same name as one of the files in folder `_data/locales`, the layout language will also be changed,
# otherwise, the layout language will use the default value of 'en'.
lang: en

# Change to your timezone › https://kevinnovak.github.io/Time-Zone-Picker
timezone: 타임존에 맞게

# jekyll-seo-tag settings › https://github.com/jekyll/jekyll-seo-tag/blob/master/docs/usage.md
# ↓ --------------------------

title: Arrow's Space # the main title

tagline: Ph.D. student's Blog # it will display as the sub-title

description: >- # used by seo meta and the atom feed
  A Ph.D. student in economics.

# Fill in the protocol & hostname for your site.
# e.g. 'https://username.github.io', note that it does not end with a '/'.
url: "https://arrow-economist.github.io"

github:
  username: arrow-economist # change to your github username

twitter:
  username: econphb # change to your twitter username

social:
  # Change to your full name.
  # It will be displayed as the default author of the posts and the copyright owner in the Footer
  name: arrow-economist
  email: arrow.economist@gmail.com # change to your email address
  links:
    # The first element serves as the copyright owner's link
    - https://twitter.com/econphb # change to your twitter homepage
    - https://github.com/arrow-economist # change to your github homepage
    # Uncomment below to add more social links
    # - https://www.facebook.com/username
    # - https://www.linkedin.com/in/username

google_site_verification: # fill in to your verification string

# ↑ --------------------------
# The end of `jekyll-seo-tag` settings

google_analytics:
  id: G-0xxxxxxxx # fill in your Google Analytics ID

goatcounter:
  id: # fill in your Goatcounter ID

# Prefer color scheme setting.
#
# Note: Keep empty will follow the system prefer color by default,
# and there will be a toggle to switch the theme between dark and light
# on the bottom left of the sidebar.
#
# Available options:
#
#     light  - Use the light color scheme
#     dark   - Use the dark color scheme
#
theme_mode: # [light | dark]

# The CDN endpoint for images.
# Notice that once it is assigned, the CDN url
# will be added to all image (site avatar & posts' images) paths starting with '/'
#
# e.g. 'https://cdn.com'
img_cdn:

# the avatar on sidebar, support local or CORS resources
avatar: "/assets/profile.jpg"

# The URL of the site-wide social preview image used in SEO `og:image` meta tag.
# It can be overridden by a customized `page.image` in front matter.
social_preview_image: # string, local or CORS resources

# boolean type, the global switch for TOC in posts.
toc: true

comments:
  active: # The global switch for posts comments, e.g., 'disqus'.  Keep it empty means disable
  # The active options are as follows:
  disqus:
    shortname: arroweconomist # fill with the Disqus shortname. › https://help.disqus.com/en/articles/1717111-what-s-a-shortname
  # utterances settings › https://utteranc.es/
  utterances:
    repo: # <gh-username>/<repo>
    issue_term: # < url | pathname | title | ...>
  # Giscus options › https://giscus.app
  giscus:
    repo: # <gh-username>/<repo>
    repo_id:
    category:
    category_id:
    mapping: # optional, default to 'pathname'
    input_position: # optional, default to 'bottom'
    lang: # optional, default to the value of `site.lang`
    reactions_enabled: # optional, default to the value of `1`

# Self-hosted static assets, optional › https://github.com/cotes2020/chirpy-static-assets
assets:
  self_host:
    enabled: # boolean, keep empty means false
    # specify the Jekyll environment, empty means both
    # only works if `assets.self_host.enabled` is 'true'
    env: # [development | production]

pwa:
  enabled: true # the option for PWA feature (installable)
  cache:
    enabled: true # the option for PWA offline cache
    # Paths defined here will be excluded from the PWA cache.
    # Usually its value is the `baseurl` of another website that
    # shares the same domain name as the current website.
    deny_paths:
      # - "/example"  # URLs match `<SITE_URL>/example/*` will not be cached by the PWA

paginate: 10

# The base URL of your site
baseurl: ""

# arrow-economist

# ------------ The following options are not recommended to be modified ------------------

kramdown:
  syntax_highlighter: rouge
  syntax_highlighter_opts: # Rouge Options › https://github.com/jneen/rouge#full-options
    css_class: highlight
    # default_lang: console
    span:
      line_numbers: false
    block:
      line_numbers: true
      start_line: 1

collections:
  tabs:
    output: true
    sort_by: order

defaults:
  - scope:
      path: "" # An empty string here means all files in the project
      type: posts
    values:
      layout: post
      comments: true # Enable comments in posts.
      toc: true # Display TOC column in posts.
      # DO NOT modify the following parameter unless you are confident enough
      # to update the code of all other post links in this project.
      permalink: /posts/:title/
  - scope:
      path: _drafts
    values:
      comments: false
  - scope:
      path: ""
      type: tabs # see `site.collections`
    values:
      layout: page
      permalink: /:title/
  - scope:
      path: assets/js/dist
    values:
      swcache: true

sass:
  style: compressed

compress_html:
  clippings: all
  comments: all
  endings: all
  profile: false
  blanklines: false
  ignore:
    envs: [development]

exclude:
  - "*.gem"
  - "*.gemspec"
  - docs
  - tools
  - README.md
  - LICENSE
  - rollup.config.js
  - package*.json

jekyll-archives:
  enabled: [categories, tags]
  layouts:
    category: category
    tag: tag
  permalinks:
    tag: /tags/:name/
    category: /categories/:name/
```

바꿔야 하는 부분이라면 우선,

1. `timezone`은 [여기](https://kevinnovak.github.io/Time-Zone-Picker)에 들어가서 본인의 타임존을 복사 후 붙여넣기 해준다.
2. `title`은 본인의 블로그 이름이다.
3. `tagline`은 블로그 이름 바로 밑에 들어가는 작은 설명란이다.
4. `description`은 블로그 설명 글귀를 적으면 된다.
5. `url`은 자기 블로그 주소를 적으면 된다. `arrow-economist` 부분에 본인의 깃허브 아이디를 넣으면 된다.
6. `social` 란은 본인의 것들을 적어주면 된다.
7. `google-analytics`를 쓴다면 이 부분을 수정해주면 된다.
8. `avatar`는 대문의 사진이다. 필자는 assets폴더에 profile.jpg로 사진을 넣어줬기 때문에 이렇게 했다. 자기 사진을 assets폴더에 넣고 파일명을 입력해주면 되겠다.
9. `comments`는 댓글기능인데, 필자는 disqus를 쓰므로 해당 shortname을 적어줬다.

# 5. git push 후 블로그 세팅 완료

이제 남은 일은 로컬에서 파일을 변경해줬으니 이것을 반영해주는 작업이다.

```
git init
```

역시 로컬폴더 경로에서 이 커맨드를 우선 실행해준다. (깃 안썼을 때 처음 하는 것으로 알고있다. 깃을 써봤다면 패스)

```
git add .
git comment -m "코맨트 남길 말 e.g. config 수정"
git push
```

이 명령어를 차례로 실행해주고, 깃허브 내 repo에서 action에 들어가면 뭔가가 돌아가고 있는 모습이 보일 것이다. 성공적으로 되었다면 초록색 불빛이 뜬다.

이제 본인의 깃허브 블로그 url로 들어가서 확인해보면 된다. 유후! 성공이다. 이제는 포스팅 하는 법을 알아야 한다.

# 6. 포스팅 하는 방법

우선 `_data/authors.yml`에 들어간다. 여기에 맨 밑에

```yml
## Template › https://github.com/jekyll/jekyll-seo-tag/blob/master/docs/advanced-usage.md#setting-author-url
# -------------------------------------
# {author_id}:
#   name: {full name}
#   twitter: {twitter_of_author}
#   url: {homepage_of_author}
# -------------------------------------

cotes:
  name: Cotes Chung
  twitter: cotes2020
  url: https://github.com/cotes2020/

sille_bille:
  name: Dinesh Prasanth Moluguwan Krishnamoorthy
  twitter: dinesh_MKD
  url: https://github.com/SilleBille/

arrow:
  name: arrow economist
  twitter: econphb
  url: https://github.com/arrow-economist/
```

이런 식으로 author를 정해주면 된다. `arrow` 부분에는 본인이 쓰고싶은 id 아무거나 적으면 되는데, 여기에 내가 `-` 이 작대기를 넣었더니 에러가 생겨서 안되었다. 참고할 부분이다.
`name`에는 이제 name을 넣어주면 되는데 내 포스팅에 `by arrow economist`이런식으로 뜨게 되는 부분이다. 일종의 서명같은 거다. `twitter`나 `url`은 자기 걸로 입력해주면 된다.

그리고 이제 `_posts` 폴더에 들어간다. 초기화를 잘 진행했다면 기존에 있었던 포스팅이 전부 날아가있을텐데, 이제 파일 하나를 생성해주겠다. vscode로

`2024-02-14-try.md`
이런 파일명으로 markdown 파일을 하나 만들어준다. [vscode로 마크다운 파일 다루는 법을 잘 모른다면 이 링크를 참고하면 된다.](https://sianux1209.github.io/etc/markdown_editor_vscode/) 여기에서 중요한 것은 맨 앞에 2024-02-14 이런 식으로 작성한 날짜를 입력해줘야 하고 그 뒤에는 영어로 적어주는 것이 낫다. 이 try가 곧 `arrow-economist.github.io/posts/try`이런 식으로 url이 되기 때문이다. 뒤에 확장자까지 잘 적어주고 파일을 생성하면 된다.

파일을 만들고 나면 맨 위에

```
---
title: jekyll chirpy theme으로 깃허브 블로그 만들기 2
author: arrow
date: 2024-02-14 23:36:00 +0800
categories: [git, github]
tags: [git, github]
---
```

이런 식으로 나오게 된다. 타이틀은 포스팅의 제목이므로 한국어로 적어도 되고 편하게 적으면 된다. author는 아까 만들어줬던 id (arrow)를 입력하면 되고, date는 YYYY-MM-DD HH:MM:TT에 맞게 입력해주면 된다. categories는 [상위폴더, 하위폴더]로 생각하면 되고, tags는 해시태그다.  
작대기 세 개 `---`도 위 아래로 잘 있어야 하므로 빼먹지 말도록 한다.

그 이후에는 마크다운 문법에 맞게 작성하면 된다.

저장까지 마치면 다시 깃 푸시 작업을 거치면 첫 번째 포스팅이 생성된다!

## 7. 생길 수 있는 에러

내가 직면했고 가장 날 괴롭혔던 에러는

```
--- layout: home # Index page ---
```

아무리 어떻게 해봐도 arrow-economist.github.io로 들어갔을 때, 위와 같은 문구만 뜨는 경우였다. 열심히 검색해본 결과 몇 가지의 해결 방법이 있었는데,

1. `bundle lock --add-platform x86_64-linux` 이 명령어를 제대로 실행하지 않았을 경우 다시 실행해보기
2. github 상의 내 repo >> settings >> pages >> build and deployment에서 source를 github actions로 바꾸기

이 정도였는데 두 경우를 다 실행해봐도 에러는 계속되었다. 하지만 나는 앞서 말했던 제일 중요한 부분인 초기화 부분에서 답을 찾았다.

3. `bash tools/init` 이 명령어를 실행을 꼭 해주자. 그래야 세팅이 되면서 구동이 가능한 것 같다. 혹시 나와 비슷한 문제로 계속 블로그가 안열린 사람이라면 이 명령어로 해결이 되길 바란다.

_에러 부분은 혹시 몰라서 이전 포스팅에 남긴 것을 그대로 가져왔다._

이제 나도 여러분도 깃허브 블로그 소유자!
