# CSS(마크업 규칙, position)

![마크업규칙](/img/마크업규칙.jpg)

1. 마크업 규칙
    - 논리적 순서를 정한다.(콘텐츠의 흐름을 고민해야 한다.)
    - 의미에 맞는 마크업을 한다.(시멘틴 마크업 / css,디자인 적인 요소를 마크업에 포함하지 말아야 한다./ 최대한 HTML 구조(문법)와 CSS를 구분.)
    - naming 작업은 class or id로 한다. name은 "단어"-"단어"로 작성한다.

2. nav는 주요 navigation 요소로 명시적으로 outline을 가지고 내부에 heading 요소를 가진다.

3. image 사용 시 alt(대체 텍스트)를 꼭 사용해야 한다.

4. 키보드 포커스를 받으려면 a 요소와 form 요소만 가능하다.  
   다만, 다른 요소도 tabindex 속성을 사용하면 포커스를 받을 수 있다.

![position](/img/position.jpg)

5. position은 부모 요소의 포지션 값이 static이 아닐때 적용된다.  
   position의 값은 relative, absolute, fixed, sticky가 있다.  
   float 속성인 요소도 position: relative는 사용할 수 있다.

![positionPadding](/img/positionPadding.jpg)

6. list 속성 중에 ul 요소와 li 요소의 관계에서  
   자식 요소 li의 방향을 적용하고 싶을 때는 부모 요소 ul에 text-align에 값을 주면 된다.

7. position 속성에서 블록 모델인 div 요소에 자식 요소 div를 추가하고 부모 요소에 padding 값을 10, 자식 요소에 padding 값을 5 주면 padding 값이 15로 적용되고 자식 요소에 있는 content는 적용된 padding 값 만큼 아래로 밀린다.  
반면 블록 모델인 div 요소에 자식 요소 span(인라인 모델)을 추가하고 부모 요소에 padding 값을 10, 자식 요소에 padding 값을 5 주면 자식 요소의 padding 값 5가 부모 요소 padding 값 10 안에 포함되고 자식 요소에 있는 content는 위치가 변경되지 않는다.

## Markup

1. 논리적인 순서 (눈에 보이는 이미지가 아닌 코드의 순서)
2. 의미에 맞는 마크업 (Semantic Markup)
3. 네이밍 (id, class)

## normalize.css

** Normalize.css는 HTML 요소의 기본 스타일을 브라우저 간 일관성을 유지하도록 돕는 CSS 파일 **

normalize cdn site : <https://cdnjs.com/libraries/normalize><br/>
normalize.css url : <https://cdnjs.cloudflare.com/ajax/libs/normalize/8.0.0/normalize.css><br/>

`사용법 : css 첫줄에 import`
<pre><code>@import url(normalize.css 경로);
</code></pre>

## css selector : nth-of-child, nth-of-type

`:nth-of-child`

- nth-of-child(n) : n번째 선택

<pre>
<code>[ CSS ]
li:nth-of-child(2) { # }

[ HTML ]
&ltul&gt
  &ltli&gt&lt/li&gt
  <span style="background-color:red">&ltli&gt&lt/li&gt</span>
  &ltli&gt&lt/li&gt
  &ltli&gt&lt/li&gt
  &ltli&gt&lt/li&gt
&lt/ul&gt
</code></pre>

- nth-of-child(n+2) : 2번째 이후 전체 선택

<pre>
<code>[ CSS ]
li:nth-of-child(n+2) { # }

[ HTML ]
&ltul&gt
  &ltli&gt&lt/li&gt
  <span style="background-color:red">&ltli&gt&lt/li&gt</span>
  <span style="background-color:red">&ltli&gt&lt/li&gt</span>
  <span style="background-color:red">&ltli&gt&lt/li&gt</span>
  <span style="background-color:red">&ltli&gt&lt/li&gt</span>
&lt/ul&gt
</code></pre>

- nth-of-child(-n+2) : 2번째 이전 전체 선택

<pre>
<code>[ CSS ]
li:nth-of-child(-n+2) { # }

[ HTML ]
&ltul&gt
  <span style="background-color:red">&ltli&gt&lt/li&gt</span>
  <span style="background-color:red">&ltli&gt&lt/li&gt</span>
  &ltli&gt&lt/li&gt
  &ltli&gt&lt/li&gt
  &ltli&gt&lt/li&gt
&lt/ul&gt
</code></pre>
- nth-of-child(n+2):nth-of-child(-n+3) : 2번째 이상, 3번째 이하 선택

<pre>
<code>[ CSS ]
li:nth-of-child(n+2):nth-of-child(-n+3) { # }

[ HTML ]
&ltul&gt
  &ltli&gt&lt/li&gt
  <span style="background-color:red">&ltli&gt&lt/li&gt</span>
  <span style="background-color:red">&ltli&gt&lt/li&gt</span>
  &ltli&gt&lt/li&gt
  &ltli&gt&lt/li&gt
&lt/ul&gt
</code></pre>

- nth-of-child(2n+1): 2n+1 등차수열로 선택 (1,3,5... 선택)
- nth-of-child(odd) : 홀수 선택
- nth-of-child(even) : 짝수 선택
- nth-of-child(n):nth-of-child(even):nth-of-child(-n+9) : 이와 같이 조건을 여러번 설정하여 선택할 수 있음


`:nth-of-type`

- nth-of-type : child 와 사용법은 동일하나, type에 따라 선택

<pre>
<code>[ CSS ]
div:nth-of-type(2) { # }
span:nth-of-type(3) { # }

[ HTML ]
&ltbody&gt
  &ltdiv&gt&lt/div&gt
  &ltspan&gt&lt/span&gt
  <span style="background-color:red">&ltdiv&gt&lt/div&gt</span>
  &ltspan&gt&lt/span&gt
  &ltdiv&gt&lt/div&gt
  <span style="background-color:red">&ltspan&gt&lt/span&gt</span>
&lt/body&gt
</code></pre>


참고 url : <http://nthmaster.com><br/>