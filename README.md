# Javascript-01
***자바스크립트는 위에서 아래로 한줄씩 읽고 순차적으로 실행되고 즉시 반환되는 인터프리터 언어(interpreted language)***
## 변수
호이스팅은 스코프 단위로 일어남 
### 변수명규칙
1. 변수명: 문자, 숫자, $
2. 첫 글자는 숫자가 될 수 없음
3. 예약어 사용 불가

### var (호이스팅 hoisting)
- 함수 스코프 (function-scoped)
1. 선언 및 초기화 단계
2. 할당 단계
```javascript
  var name;
  console.log(name); //undefined 값 할당 안됨x
  name = 'Mike'; //할당시작
```

### let  (Temporal Dead Zone 영향받음)
- 블록 스코프(block-scoped)
1. 선언 단계
2. 초기화단계
3. 할당단계

### const (Temporal Dead Zone 영향받음)
- 블록 스코프(block-scoped)
1. 선언 단계 + 초기화 + 할당
```javascript
  //Block Scoped : 지역변수
  //함수, if문, for문, while문, try/catch 문 등
  function add() {
    // Block-level Scope
  }
  if() {
    //Block-level Scope
  }
  for(let i=0;i<10;i++){
    //Block-level Scope
  }

  //Function-scoped : 함수에서 선언한 변수만 그 지역변수로 됨
  //var 유일하게 벗어날수 없는 스코프가 함수 스코프임
  const age = 30;
  if(age>19) {
    var txt = '성인';
  }
  console.log(txt); //성인
```  


## \특수문자
```plaintext
  'i\'m a boy'
  `${변수명}`
```

## typeof : 데이터 타입을 문자열로 반환
```javascript
  //number
  console.log(typeof 3);

  //string
  console.log(typeof name);

  //boolean
  console.log(typeof true);

  //string
  console.log(typeof "xxx");

  //object
  console.log(typeof null);

  //undefined
  console.log(typeof undefined);

  //숫자 -> 숫자 + 문자 = 문자
```

## prompt(), alert(), confirm(), String()
- 실행시 스크립트 일시 정지됨
- 스타일 적용불과, 브라우저 내장된 스타일
### prompt()
```javascript
  const name = prompt('이름을 입력해주세요');
  alert("환영합니다 "  + name + " 님"); //표기 1
  alert(`환영합니다, ${name}님`); //표기 2

  prompt("예약일을 입력해 주세요", "2024-03-");
```
***나이입력 -> prompt 취소클릭 -> null -> Number(null)은 0 임 ->0 으로 반환됨***
### confirm()
```javascript
  //true = 확인, false = 취소
  confirm("예약을 취소하시겠습니까?");
```
### String()
- 문자열

### Number()
- 숫자
- Number(null) = 0
- Number(undefinded) = NaN

### Boolean()
```plaintext
  - true (1) / false (0)
  - false = 0, "", null, undefined, NaN

  Boolean(0) -> false
  Boolean('0') -> true
  Boolean('') -> false
  Boolean(' ') -> true
```

## 기본연산자 Operators (+ - * %)
- 홀수 x % 2 = 1
- 짝수 Y % 2 = 0
```javascript
  //어떤값이 들어와도 5를 넘기면 안됨
  const num = X % 5 //= 0 ~ 4 사이 값만 반환

  //거듭제곱
  const num = 2 ** 3 //= 8

  //변수에 5를 증가시켜서 다시 변수에 넣어줌
  let num = 10
  num = num + 5
  num += 5

  //증가연산자
  let num = 10
  let result = num ++ //10
  let result = ++num //11
```

## 비교 연산자 (< > <= >= == === !=)
## 논리연산자 || && ! (or And Not)
&& 이 || 보다 편가 우선순위가 높음

## 반복문 for
### break: 멈추고 반복문 빠져나옴
### continue: 멈추고 다음 반복으로 진행
```javascript
  for(let i = 0; i < 10; i ++){
    //반복할 코드
  }

  //continue 예제 : 0 2 4 6 8 짝수 반환
  for(let i = 0;i < 10; i ++){
    if(i%2){
    continue;
    }
  console.log(i)
  }
```

## while문
### break: 멈추고 반복문 빠져나옴
### continue: 멈추고 다음 반복으로 진행
```javascript
  let i = 0;
  while(i < 10) {
    //실행코드 만 입력시 무한반복함으로 
    i++ //i를 1씩 증가 시켜줌 
  }

  //confirm 확인 클릭시 무한반복, 취소 클릭시 break 반복 끝
  while(true){
    let answer = confirm("계속 진행 하겠습니까?");
    if(!answer){
      break;
    }
  }
```

## do..while문
### break: 멈추고 반복문 빠져나옴
### continue: 멈추고 다음 반복으로 진행
```javascript
  let i = 0;
  do {
    //실행코드
    i++
  }while (i < 10)
```
## switch문
### switch문 if문 비교코드
***if문 else = switch문 default***
```javascript
  //switch문
  switch(평가){
    case A :
      //A일때 코드
      break;
    case B :
      //B일때 코드
      break;
    case C :
      //C일때 코드
      break;
  }

  //if문
  if(평가 == A){
    //A일때 코드
  }else if(평가 == B){
    //B일때 코드
  }else{
    //C일때 코드
  }
```
```javascript
  //결과 값이 같을땐 수박 멜론 처럼 작성가능
  // 사용자가 prompt에 바나나 입력했다 가정시, break;를 입력 안한 코드는 200 300 500 500 바나나 이후 값도 다 반환됨
  let fruit = prompt("무슨 과일을 구매하고 싶나요?");
  switch(fruit){
    case '사과' :
      console.log('100원 입니다.');
      break;
    case '바나나' :
        console.log('200원 입니다');
        break;
    case '키위' :
        console.log('300원 입니다');
        break;
    case '수박' :
    case '멜론'
        console.log('500원 입니다');
        break;
    default :
        console.log('그런 과일은 없습니다.');
  }
```

## function 함수
```plainText
  네이밍예시
  - showError //에러를 보여줌
  - getName //이름을 얻어옴
  - creatUserData //유저데이터 생성
  - checkLogin //로그인 여부 체크
```
```javascript
//함수 함수명 매개변수: 없을 수 있고 여러개일 수 있고 여러 개일 때 ,로 구분
  function sayHello(name) {
    console.log("Hello, ${name}");
  }

  //반환값: Hello, Mike
  function sayHello(name){
    const msg = `Hello, ${name}`;
  }
  sayHello('Mike');

  //반환값: 
  function sayHello(name){
    console.log(name) //undefined
    let msg = `Hello`;
    if(name){
      msg = `Hello, ${name}`;
    }
  }
  sayHello();

  //반환값: 
    function sayHello(name){
      console.log(name) //undefined
      let msg = `Hello`;
      if(name){
        msg += `, ${name}`;
      }
    }
    sayHello();
    sayHello('Mike');
```
### 전역 변수, 지역 변수 
```javascript
  //예시 1
  let msg = "welcome";
  console.log(msg) // "welcome"

  function sayHello(name){
    let msg = "Hello";
    console.log(msg + ' ' + name); //"Hello Mike" 
  }

  sayHello('Mike');
  console.log(msg) //"welcome"

  //예시 2
  let name = "Mike";

  function sayHello(name){
    console.log(name);
  }

  sayHello(); //undefined
  sayHello('Jane'); //Jane
```
```javascript
  //예시 
  function sayHello(name){
    let newNams = name || 'friend'; 
    let msg = `Hello, ${newName}`;
    console.log(msg)
  }
  sayHello(); //"Hello, friend"
  sayHello('Jane'); //"Hello, Jane" (name=false, 'friend'=true)

  //예시 코드정리: 기본값설정
  function sayHello(name = 'friend'){
    let msg = `Hello, ${name}`
    console.log(msg)
  }
  sayHello();
  sayHello('Jane');
```
### return으로 반환
***return문은 오른쪽 값은 반환하고 종료하기 때문에 함수 종료목적으로 returnd을 입력 하기도함***
***return; 다음 실행문은 함수가 종료 되기 때문에 절대 실행되지 않음***
```javascript
  function add(num1, num2) {
  return num1 + num2;
  }
  const result = add(2, 3);
  console.log(result); //5
```

## 함수 표현식 & 화살표 함수
### 함수 선언문 & 함수 표현식
```javascript
  //함수 선언문: 어디서든 호출 가능
  // sayHello(); 위에 호출해도 가능 (호이스팅 hoisting)
  /*
    자바스크립트는 위에서 아래로 한줄씩 읽고 순차적으로 실행되고 즉시 반환되는 인터프리터 언어(interpreted language),
    하지만 함수 선언문 위에 호출하면 어떻게 실행되는걸까?
    자바스크립트 내부 알고리즘은
    실행전 초기화 단계에서 코드의 모든 함수 선언문을 찾아서 생성해둠
    그래서 함수호출이 함수선언문 위에 있어도 실행됨
    눈으로는 안보이지만 사실상 함수선언문들이 코드 최상단에 있는것
  */
  
  function sayHello(){
    console.log('Hello');
  }
  sayHello();

  //함수 표현식: 이름 없는 함수를 만들고 변수 선언해 함수를 할당해줌
  //호이스팅 안됨
  let sayHello = funtion() {
    console.log('Hello');
  }
  sayHello();
```
### 화살표 함수 (arrow function)
```javascript
  //함수 표현식 
  let add =  function(num1, num2){
    return num1 + num2;
  }

  //화살표 함수
  let add =  (num1, num2) => {
  return num1 + num2;
  }
  //화살표 함수: 본문이 한줄이고 return문이기에 아래처럼 작성가능 :{}을 ()로
  let add = (num1, num2) => (
    num1 + num2;
  )

  //화살표 함수: return문이 한줄이면 ()도 생략가능
  let add = (num1, num2) => num1 + num2;

  //화살표 함수: 인수가 하나면()생략가능
  let sayHello = name => `Hello, ${name}`;

  //화살표 함수: 인수없으면 ()생략불가
  let showError = () => {
    alert('error!');
  }
  //화살표 함수: return문이 있다고 해도 코드가 여러줄이면 {}를()로 사용불가
  let add = (num1, num2) => {
    const result = num1 + num2;
    return result;
  }
```
## 객체 Object
***키(key) : 값(value)***
```javascript
  const superman = {
    name: 'clark',
    age: 33,
  }
```
```plaintext
  <접근>
  superman.name //clark
  superman['age'] //33
  <추가>
  superman.gender = 'male';
  superman['hairColor'] = 'black';
  <삭제 : delete 키워드>
  delete superman.hairColor;
```
### 단축 프로퍼티
***in연산자로 프로퍼티 확인가능 : 함수 인자로 받거나 API통신을 통해 DATA를 받을때 사용***
```javascript
  const name = 'clark';
  const age = 33;
  const superman = {
    name, // name: name,
    age, // age: age
    gender: 'male',
  }
  //superman.birthDay -> undefined:존재하지 않는 프로퍼티
  //'birthDay' in superman; -> false
  // 'age' in superman; -> true
```
### 객체를 반환하는 함수 
```javasscript
  function makeObject(name, age) {
  return {
    name: name, //name, 축약해서 사용가능
    age: age,  //age, 축약해서 사용가능
    hobby: 'fooball'
    }
  }
  const Mike = makeOject('Mike', 30);
  console.log(Mike);
  console.log('age' in Mike); //true
  console.log('birthday' in Mike); //false
```
### age정보가 있는지 나이는 20살 이상인지 확인 함수
```javascript
  function isAdult(user) {
    if(!('age' in user) || age < 20){ //user에 age가 없거나 20살 미만이면 false
      return false;
    }
    return true;
  }
  const Mike = {
    name: 'Mike',
    age: 30,
  }
  const Jane = {
    name: 'Jane',
  }
  console.log(isAdult(Mike)); //true
  console.log(isAdult(Jane)); //false
```
### for...in반복문
***객체를 순회하면서 값을 얻어올 수 있음***
```javascript
  for(let key in superman){
    console.log(key)
    console.log(superman[key])
  }
```javascript
  const Mike  =  {
    name: 'Mike',
    age: 30
  };
  for(x in Mike) { //x는 원한는 작명가능
    console.log(x) //"name" "age"  : 키값반환
    console.log(Mike[x]) //Mike['name'] 이렇게 한번 돌고 Mike['age'] 를 돌음
  }
```

### 객체에 함수 호출
***method: 객체 프로퍼티로 할당된 함수***
```javascript
  //같은코드 작성1
  const superman = {
    name: 'clark',
    age: 33,
    fly: function(){
      console.log('날아갑니다.')
    }
  }
  //같은코드 작성2
  const superman = {
      name: 'clark',
      age: 33,
      fly(){
        console.log('날아갑니다.')
      }
    }
  superman.fly(); //날아갑니다
```  
```javascript
  const ueser = {
    name : 'Mike',
    sayHello: function() {
      console.log('Hello, I'm ${this.name}');
    }
  }
  user.sayHello(); //Hello, I'm Mike


  let boy = {name: 'Mike',sayHello}
  let girl = {name: 'Jane',sayHello}
  sayHello: function(){
    console.log(`Hello, I'm ${this.name}`);
  }
  //화살표함수는 자신만의 this를 가지지 않음 그래서 this 사용시 전역객체를 불러오게됨(브라우저환경:window, Node js환경: global) 
  boy.sayHello(); //I'm Mike
  girl.sayHello(); //I'm Jane  
```
## 배열 Array 
- 순서가 있는 리스트 (index는 0부터 시작)
- length: 배열의 길이 반환 (students.length)
- push(): 배열 끝에 추가*
- pop(): 배열 끝에 요소 제거
- shift(): 배열 앞에 제거*
- unshift(): 배열 앞에 추가
```javascript
  //1~30번 학생 있다 가정
  let students = ['철수', '영희', ...'영수'];
  console.log(students[0]); //철수
  console.log(students[1]); //영희
  console.log(students[29]); //영수

  student[0] = '민정'; //수정 가능
  console.log(students) //['민정','영희'...]
```
***배열은 문자 뿐만 아니라, 숫자, 객체, 함수 등도 포함할 수 있음***
```javascript
  let arr = [
    '민수',
    3,
    false,
    {
      name: 'Mike',
      age: 30,
    },
    function(){
      console.log('TEST');
    }
  ];
```
```javascript
  //push() : 배열 끝에 추가
  let days = ['월', '화', '수'];
  days.push('목');
  console.log(days) //['월','화','수','목']
```
```javascript
  //pop() : 배열 끝에 요소제거
  let days = ['월', '화', '수'];
  days.pop();
  console.log(days) //['월','화']
```
```javascript
  //unshift(): 배열 앞에 추가
  let days = ['월', '화', '수'];
  days.unshift('일');
  console.log(days) //['일','월','화','수'];

  //shift(): 배열 앞에 제거
  days.shift();
  console.log(days) //['월','화','수'];

  //여러요소 한번에 추가가능
  let days = ['월', '화', '수'];
  days.unshift('금','토','일');
  console.log(days) //['금','토','일','월','화','수'];
```
```javascript
  //반복문 for
  let days = ['월','화','수'];
  for(let idx = 0; idx < days.length; idx++){
    console.log(days[idx]); //0~2까지 반복 '월''화''수' 반환
  }
```
```javascript
  //반복문 for...of
  let days = ['월','화','수'];
  for(let day of days){
    console.log(day); //index 는 못 얻음 , '월''화''수' 반환
  }
```







