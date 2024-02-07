---
title: Scroll table
excerpt: 스크롤가능한 table

categories:
    - vue
---

웹 포트폴리오 제작 중  
스크롤이 가능한 테이블이 필요해 여러가지 찾아보고 섞어서 꽤 괜찮은 방법이 나온것 같아  
블로그에 남겨두기로 하였다.

```css
  /*
    padding 순서 : top right bottom left;
  */

  padding: 0px calc(40px - $scroll-bar-width) 0px 40px;
  color: var(--vt-c-black);

  table{
    width: 100%;
  }

  thead{
    display: table;
    width: calc(100% - ($scroll-bar-width));
  }

  tbody{
    display: block;
    max-height: 70rem;
    overflow-y: scroll;

    /*
      scrollbar design : -webkit-scrollbar
      webkit browser에서만 유효(크롬, 사파리 등)

      ::-webkit-scrollbar	-> 스크롤바 전체
      ::-webkit-scrollbar-thumb	-> 스크롤 막대
      ::-webkit-scrollbar-track	-> 스크롤 막대 외부

    */

    &::-webkit-scrollbar{
      width: $scroll-bar-width;
    }

    /*
      thumb와 track사이에 공간(padding)을 주고 싶을 때는 
      thumb의 background-clip을 padding-box로 설정하고, border 색상을 transparent(투명)으로 조절
    */

    &::-webkit-scrollbar-thumb{
      background-color: cyan;
      border-radius: 5px;
      background-clip: padding-box;
      border: 1px solid transparent;
    }

    &::-webkit-scrollbar-track{
      background-color: blanchedalmond;
      border-radius: 5px;
    }
  }
```

디자인적으로 중요한것은 ``thead``의 ``width``를 스크롤의 크기만큼 계산하여 책정하는 것이다.

```css
width: calc(100% - ($scroll-bar-width));
```

또한 전체적인 ``padding`` 또한 스크롤바의 크기를 고려하여 설정하는것도 중요하다.