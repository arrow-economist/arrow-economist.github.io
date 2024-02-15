---
title: 깃허브 블로그에 후원버튼 다는 방법
author: arrow
date: 2023-04-07 00:34:00 +0800
categories: [Git, Github]
tags: [github]
---

# #Github #Buymeacoffee #Donation

블로그를 만들어 글을 쓰는 가장 큰 이유는 내가 필요할 때 찾아보고 정보를 잊지 않기 위해서가 가장 크다. 하지만 후원이라는 인센티브가 있다면 그 또한 글 쓰는 즐거움이 아닐까? 그래서 후원 받는 버튼을 다는 방법을 열심히 찾아보았다. 하지만 생각보다 잘 나오지 않았고, 에러가 계속 나오던 끝에 드디어 후원 링크를 다는 방법을 터득했다. 이 글은 나같이 Git이고 Github고 html이고 아무것도 모르는 사람 기준으로 작성해보았다.

우선 도네이션을 어떻게 받을 지를 결정해야 한다. 필자의 경우는 **Buy me a coffee**와 **카카오페이**를 이용하기로 했다.

### 1. **Buy me a coffee** 가입하기

개발자 분들의 블로그를 보면, 아니면 깃허브 같은 곳을 보면 가장 많이 보이는 도네이션 플랫폼이 Buy me a coffee인 것 같다. 우선 [Buy Me A Coffee](https://www.buymeacoffee.com/signup)를 들어가서 회원가입을 한다. 구글계정으로 가입하면 간단한 설정과 함께 가입이 금방 끝난다.

![가입된 모습](https://raw.githubusercontent.com/arrow-economist/arrow-economist.github.io/master/images/Donation1.png)

가입을 마치면 이런 화면이 뜬다. 나는 간단히 페이지도 꾸며보았다. 그러면 오른쪽 상단의 프로필을 클릭 후 **Dashboard**를 클릭하면 세팅 창이 나오는데, 여기에서 **Share pages**를 누르고 copy link를 하면 내 후원 링크가 복사가 된다. 하지만 우리는 아직 github page를 수정해야하니 아직 복사는 하지 않도록 한다.

### 2. Github *\_sass*폴더 수정하기

이 글을 찾아보지도 않고 알아서 척척 하시는 분들은 Jekyll Themes 없이도 Github page를 잘 만드시는 분들일테니, 그 분들을 제외한다면 아마 웬만하면 전부 Jekyll Themes를 이용해서 블로그를 만드셨을 것이다. 필자도 minimal-mistakes 테마를 이용해서 만들었고 하나씩 배워가면서 수정 중에 있다. 여기에서는 **minimal-mistakes** 테마에 맞춰서 설명을 하도록 하겠다. 다른 테마는 이와 좀 다를 수 있다.

*\_sass>minimal-mistakes>\_utilities.scss*는 아마도? Visibility를 관리하는 파일인 것 같다. 여기에 들어가서 다음과 같은 코드를 맨 위에, 주석 빼면 **11번째 줄**에 작성을 해주면 된다.

```css
.fa-coffee {
  color: $background-color;
}

.fa-comment {
  color: $background-color;
}
```

코드를 내가 아는 한에서 설명을 해보자면, 후원버튼에 아이콘? 혹은 이모지를 넣고 싶은데 그걸 [여기](https://www.w3schools.com/icons/fontawesome5_intro.asp)에서 끌어오는 것 같다. *fa-coffee*는 커피모양이고 *fa-comment*는 카카오톡 말풍선 모양이다.

이렇게 바꾸고 난 후에는 *\_sass>minimal-mistakes>\_buttons.scss*에 들어간다. 특별히 수정한게 없다면 **31번째 줄**부터 다음과 같은 코드가 있을 것이다.

```css
/* button colors */
$buttoncolors: (primary, $primary-color), (inverse, #fff),
  (light-outline, transparent), (success, $success-color),
  (warning, $warning-color), (danger, $danger-color), (info, $info-color), (
    facebook,
    $facebook-color
  ), (twitter, $twitter-color), (linkedin, $linkedin-color), (coffee, #cf7dff), /* 추가해야 하는 부분 */
    (comment, #fddc3f); /* 추가해야 하는 부분 */
```

원래는 *linkedin*까지만 작성이 되어있겠지만 이 밑에 나는 *coffee*와 _comment_ 명령어를 추가해줬다. 색상표는 구글에 검색하면 나오는데, *coffee*는 연보라색쪽이고 *comment*는 노란색이다. 이 때 *linkedin*명령어 다음에 쉼표와 명령어 마지막 ;에 주의하자! 나는 _linkedin_ 명령어 다음에 쉼표(,)를 빼먹어서 몇 시간동안 에러를 찾느라 애를 썼다. ~~(진짜 초보)~~

이렇게까지 하면 준비는 끝났다.

### 3. _\_layouts_ 폴더 수정하기

이제 메인으로 돌아가서 _\_layouts_ 폴더에 들어간다. 그러면 *single.html*이 있는데, 이 것을 수정해줘야 한다. 특별히 수정을 하지 않았다면 **50번째 줄** 밑에 section이 끝나는 `</section>` 바로 위에 추가를 해주면 된다.

```html
<div id="buy-me-a-coffee-btn">
  <a href="https://www.buymeacoffee.com/arroweconomist" class="btn btn--coffee">
    <i class="fa-fw fas fa-coffee" aria-hidden="true"></i>
    <span>Buy me a coffee ❤️</span>
  </a>
</div>
<div id="kakaopay-btn">
  <a href="https://qr.kakaopay.com/Ej7nznEoP" class="btn btn--comment">
    <i class="fa-fw fas fa-comment" aria-hidden="true"></i>
    <span>Kakaopay Donation</span>
  </a>
</div>
```

여기에서 `<a href="https://`부분에 아까 1번에서 복사를 하려고 했던 buy me a coffee의 후원링크 주소를 달면 된다. 추가로 나는 카카오페이도 넣었는데, 카카오페이는 **카카오톡 접속 - 더보기 - 코드스캔 - 송금코드**에 들어가면 링크를 복사할 수 있다. 수정을 마치고 남은 일은 이제 가운데 정렬만 하면 된다.

### 4. _\_sass/minimal-mistakes/page.scss_ 수정하기

여기에서는 가운데 정렬을 할 것이다. 역시 아무 것도 수정하지 않았다면, 그 기준으로 **22번째 줄**부터 다음과 같은 코드가 있다.

```css
body {
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  min-height: 100vh;
  -webkit-box-orient: vertical;
  -webkit-box-direction: normal;
  -ms-flex-direction: column;
  flex-direction: column;
}
/* 추가해야하는 부분 */
div#buy-me-a-coffee-btn {
  text-align: center;
  margin-top: 3em;
}

div#kakaopay-btn {
  text-align: center;
}
/* 추가해야하는 부분 */
```

추가해야하는 부분을 그대로 복사해서 위치에 붙여넣기를 하자. margin-top은 본인이 원하는 만큼으로 수정을 해주면 되는데 나는 3으로 설정했다.

그러면 이제 이 포스팅의 지금 하단처럼 후원 버튼이 나타나게 된다! 나는 나란히 정렬을 하고 싶지만 그 방법은 아직 모르겠다. 찾는 대로 추가해야겠다.

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEyODM5NTA5NzUsLTU4MDE4MzA1MSwxND
Q3NDQ5MzAsNTE4NDc1NDQ2LDEyNzczNjk5MTIsOTYwNDg5NDU3
LDg4MjQ4NzQ2OSw2MTM4NjcwMzMsLTk1MTE1MTUyNSwyMDk5Mz
czODUxLDg4MjQ4NzQ2OSw3NTgyNDE1ODYsLTgzODM1NTYzOCwy
NzI3NDk1NjcsLTkwODMwNjU3LDc4MzgzMzg3LC0zNzM4NDE3MT
csLTE3MTM2MTA4MDMsMTc3MzQ0NjQyMCw4MTYxNjU5Ml19
-->
