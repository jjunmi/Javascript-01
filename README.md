# Javascript-01

## 변수
1. 변수명: 문자, 숫자, $
2. 첫 글자는 숫자가 될 수 없음
3. 예약어 사용 불가

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
```





