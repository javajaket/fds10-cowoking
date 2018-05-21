180521-수업내용
===
viewport를 통해 각각 사이즈 변경 가능
---
device-width
- 기기 독립적 픽셀에서 화면 너비에 맞게 페이지를 맞춘다.
- 렌더링되는 화면이 작은 휴대폰이든 큰 데스크롭 모니터에는 상관없이, 다양한 화면 크기에 맞게 페이지의 콘텐츠를 재배치 할 수 있다.

media query
- 미디어 타입과 같이 폭,높이,색깔과 같이 디바이스의 특성을 이용해 스타일시트의 적용범위를 제한하는 하나이상의 식으로 구성
- 컨텐츠를 각 디바이스의 출력폭에 맞춰 표시하는 것이 가능
---
 컨텐츠 준비 
---
  - 논리적인 준비,순서(어떤 것을 먼저 마크업 할건지 준비)
    - 로그인
    - 아이디(이미지or텍스트)
    - 비밀번호,로그인 버튼
    - 회원가입/아,비찾기 링크
  - 시맨틱 마크업(의미에 맞는 마크업,기계에 맞추는 마크업)
    - div/section/article
    - form태그 : <br>
      - 사용자 입력을 위한 다양한 형힉의 컨트롤로 구성되는 영역, 이 영역의 <br>
        시작과 종료 지점은 form 요소에 의해 정의
      - `fieldset`(=div) : <br>
        1.의미있게 묶어주는 역할,여러개 생성해도 괜찮음(제한없음)<br>
        2.fieldset안에 fieldset를 또 넣을 수 있음<br>
      - `action` : 실행 애플리케이션을 지정 <br>
        입력된 데이터를 처리하는 서버 또는 프로그램,이곳으로 데이터를 보내려면 브라우저가 전송위치(URL)룰 알아야 하며, 이를 위해 action 속성을 사용
      - `legend` : fieldset 요소의 제목(legend) 을 표시<br>
        fieldset요소를 이용하려면 여러 개의 컨트롤들을 묶었으면 <br>이 묶음이 어떤 성격 또는 용도인지 알려줄 필요가 있다.
      - `label` : 아이디 , input : (아이디 입력) <br>
        컨트롤 요소를 요소 안에 배치하거나 for속성을 사용하여 컨트롤과 연결 가능
        - 암묵 : label안에 id를 집어넣어 암묵적으로 id라고 안내
        - 명시 : for를 통해 id라고 설정해준다.
        - type="" 공백안에 타입형식 설정 가능
        - 레이블이 입력형식과 이어졌는지 확인해보기
        - input : inline-block 형식 
      - `input type=""` : empty 요소,value="" 값을 찾아 수정해야 한다.
      - `button type=""` 
      - `input type="email"` : 이메일형식이 아닐경우 창이 뜬다. web forms 2.0때 만들어짐
      - `maxlength="(숫자)"` : 입력할수 있는 칸 단위
      - `required` : 필수 항목 설정
      - `placeholder="kt5161497@gmail.com"` : 예시값 알려주기
      - `title="8자리 이하"` : 툴팁형태로 나타남,마우스를 갔다되면 나타남
##### https://formspree.io/  
##### html태그에서 width,height 사이즈 조절 할 경우 디폴트값이 px이므로 뒤에 붙이지 말기
#### https://caniuse.com/ 에서 자주 검색해보기

.login-form [type="email"], .login-form [type="password"]{
  width: 100px;
  height: 25px;
}
- [type="email"],[href=^http://] 등 여려가지 방법으로 설정가능하다.
- tarket="_blank" : 새창으로 띄운다.
- title="(대체설명)"는 a 태그와 잘 어울린다. 

dl 태그 : 정의형 태그
- dt : 용어 이름
- dd : 용어 설명
##### dl 태그안에 div 태그가 올수 없다. but dt와 같이 묶어서 div 태그를 묶어 된다.
##### https://mulder21c.github.io/2017/12/26/understanding-html-52-changes/
###### https://www.miketaylr.com/pres/html5/forms2.html

index.html 레이아웃
===
    <section class="login">
          <h2 class="login-heading">로그인</h2>
          <form method="POST" action="https://formspree.io/kt5161497@gmail.com" class="login-form">
            <fieldset>
              <legend>회원 로그인 폼</legend>
              <div class="user-id">
                <label for="user-id">아이디</label><input type="email" id="user-id" name="id" required placeholder="ID or Email" size="15">
              </div>
              <div class="user-pw"><label for="user-pw">비밀번호</label><input type="password" id="user-pw" name="pw" maxlength="8" required placeholder="8자리 이하"></div>
              <button type="submit" class="btn-login">로그인</button>
              <!-- submit: 폼이 가지고 있는 액션으로 보낸다. -->
            <!-- div.user-id>label[for="user-id"]{아이디}+input#user-id // inline상자 -->
              <!-- <label for="user-id">아이디</label>
              <input type="text" id="user-id"> -->
              <!-- <input type="text" id="user-id" size="50"> -->
              <!-- label+input#user-id -->
              <!-- 띄어쓰면 공백이 생김 -->
            </fieldset>
          </form>
          <ul class="sign">
            <li><a href="#" class="icon-right-open">회원가입</a></li>
            <li><a href="#" class="icon-right-open">아이디/비밀번호 찾기</a></li>
          </ul>
        </section>
        <h2 class="readable-hidden">유효성 검사 배너</h2>
        <ul class="validation-list">
          <li>
            <a href="https://validator.w3.org/" target="_blank" title="마크업 유효성 검사 사이트로 이동">W3C Markup Validation</a>
          </li>
          <li>
              <a href="https://jigsaw.w3.org/css-validator/" target="_blank" title="CSS 유효성 검사 사이트로 이동">CSS Validation Service</a>
          </li>
        </ul>
        <section class="term">
          <h2 class="term-heading">웹 관련 용어</h2>
          <dl class="term-list">
            <dt class="term-list-subject">웹 표준 이란?</dt>
            <dd class="term-list-thumbnail">
              <img src="images/web_standards.gif" alt="웹 표준 관련 기구인 W3C의 새로운 로고">
            </dd>
            <dd class="term-list-brief">
                W3C 단체에서 규정한 웹 기술 사양에 대한 규칙을 말하며 표준 규격은...
            </dd>
          </dl>
        </section>
    
