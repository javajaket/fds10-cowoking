180605 - 수업 내용
===
- Host object : 
- Native object : method가 무엇이 있는지 알아야 한다.
-----
# String
 - wrapper : 기본자료형에 .을 찍으면 객체처럼 사용가능하다. 순간적으로 객체로 된다. null,undefined는 wrapper가 없다. 만약 .을 찍을 경우 error가 출력된다.
 - String Constructor : 생성자 객체만 프로토타입을 가지고 있다.
 - new String(value); : 생성자 함수에 인수를 주는 이유 -> 프로퍼티의 초기화 값(value)

 <pre>
 var strObj = new String('Lee'); 
// 문자열은 객체가 되었을 때 유사배열된다. length가 있어야 for문을 돌릴 수 있다.
console.log(strObj); // String {0: 'L', 1: 'e', 2: 'e', length: 3, [
// [[primitiveValue]] : 함부로 접근하지 말라는 뜻
[PrimitiveValue]]: 'Lee'}
 </pre>
 <pre>
 var strObj = new String(1); 
 //숫자열이면 문자열로 바꾼다. 
console.log(strObj); // String {0: '1', length: 1, [[PrimitiveValue]]: '1'}
 </pre>
 <pre>
 var strObj = new String(undefined);//문자열로 강제 전환
console.log(strObj);
 </pre>
 <pre>
 var x = String('Lee'); 
// 앞에 New를 안붙이면 String(문자열)로 변경되어 넘어 온다.
console.log(typeof x, x); // string Lee
 </pre>

# String.length 
<pre>
str = '안녕하세요'; //유니코드 사용
console.log(str.length); // 5
</pre>

# String Method 

- String 객체의 모든 메소드는 언제나 새로운 문자열을 반환한다. 문자열은 <br>
  immutable한 값이기 때문이다.

# String.prototype.charAt(pos: number): string

- prototype method
- at : 위치정보를 return 해주는 의미
-----
### 문제) 1~10000의 숫자 중 8이 증장하는 횟수 구하기
- 1부터 10,000까지 8이라는 숫자가 총 몇번 나오는가? 이를 구하는 함수를 완성하라.<br>
  단, 8이 포함되어 있는 숫자의 갯수를 카운팅 하는 것이 아니라 8이라는 숫자를 모두<br> 카운팅 해야 한다. 예를 들어 8808은 3, 8888은 4로 카운팅 해야 한다.
  
<pre>
function getCount8(){

  var str = '';
  for(var i = 0; i<10000;i++){
    str += i;  
  }
  var count = 0;
  for(var j = 0; j < str.length;j++){
    // j ==> 0, 1, 2,
    //str[j] 문자열 '0'
    if(str[j] === '8'){
      count++;
    }
  }  
  return count;
}
console.log(getCount8()); 
</pre>

#  String.prototype.concat(…strings: string[]): string
<pre>
var str = 'Hello ';
var name = 'Lee';

str = str.concat(name); // str = str + name; 오른쪽이 가독성 더 좋다.
//str의 name을 연결한다.
console.log(str); // Hello Lee
</pre>

# String.prototype.indexOf(searchString: string, fromIndex=0): number
- index의 위치를 알수 있다. 
- str.indexOf(searchString[, fromIndex]) <br> 
  formIndex : 처음 위치 설정 

# String.prototype.replace(searchValue: string | RegExp, replaceValue: string): string

- 첫번째 인자에 전달된 무자열 또는 정규표현식을 대상 문자열에서 검색하여 두번째 인자에 전달된 문자열로 대체한다.

# String.prototype.substring(start: number, end=this.length): string

- 필요한 문자만 뜯어내는 것

String은 항상 결과값을 반환해야 한다.

### 문제 전화번호 뒤에서 4번째까지만 숫자 노출
<pre>
function hideNumbers(str) {
  var len = str.length - 4;
  var star = '';
  for(var i = 0; i < len; i++){
    star += '*';
  }
  // '*'.repeat(len);
  return star + str.substring(len);
}

console.log(hideNumbers('010å33334444'));
console.log(hideNumbers('027778888'));
</pre>

Number
===
# Number.EPSILON
<pre>
console.log(0.1 + 0.2);  // 0.30000000000000004,무한소수가 되어 오차 발생
console.log(0.1 + 0.2 == 0.3); // false!!!
</pre>

# Number.isFinite(testValue: any): boolean
- 전달된 값이 정상적인 유한수인지를 검사하여 그 결과를 Boolean으로 반환한다.
- Number.isFinite()는 전역 함수 isFinite()와 차이가 있다. 전역 함수 isFinite()는 인수를 숫자로 변환하여 검사를 수행하지만 Number.isFinite()는 인수를 변환하지 않는다. 따라서 숫자가 아닌 인수가 주어졌을 때 반환값은 언제나 false가 된다.

- static method : 언제든지 호출 할수 있다.
- prototype method : 객체를 만든 후 호출 할 수 있다.
<pre>
Number.isFinite(Infinity)  // false, 형변환을 안한다.
//Number 생성자의 isFinite 메써드를 호출하였다.
isFinite() //  형변환을 한다.
</pre>
<pre>
var num = 123;
num.isFinite(); // 프로토 타입으로 접근하기 때문에 에러
</pre>

# Number.prototype.toFixed(digits=0): string
- 반올림한다.

## 3번 문제
<pre>
function alphaString46(s){
  //s가 undefined이면 false를 반환
  if(!s) return false;
  return (s.length >= 4 && s.length <=6) && !isNaN(s);
  // if((s.length >=4 && s.length <=6) && !isNaN(s)){
  //   return true;
  // }else {
  //   return false;
  // }
}
console.log(alphaString46('1234'));
console.log(alphaString46('9014'));
console.log(alphaString46('723'));
console.log(alphaString46('a234'));
console.log(alphaString46(''));
console.log(alphaString46());
</pre>

Date 
===
- 날짜,시간,요일등 가지고 있다.
- setTimeout(printNow,1000);
- 함수 재귀적 사용
<pre>
setTimeout(printNow,1000);
// 첫번째 함수: 콜백,두번째 함수: 1초마다 함수를 호출한다.(함수를 1초에 한번씩 부른다.)
</pre>


