# 자바스크립트란?
HTML은 구조, CSS는 디자인, 그리고 자바스크립트(JavaScript)는 동작을 담당한다고 생각하면 쉽다. 자바스크립트 프레임워크인 리액트(React), 뷰(Vue.js), 앵귤러(Angular)를 제대로 활용하기 위해서 자바스크립트의 이해는 필수이며 프론트엔드 뿐만 아니라 백엔드 개발자에게도 중요하다고 말하기에 입아픈 언어라고 할 수 있다.

* HTML 외부에 자바스크립트를 기술하고 싶을 때는 `<script src="자바스크립트파일명.js"></script>` 해당 코드로 불러옵니다.

# 변수 let과 상수 const
let은 데이터 값 변경이 가능한 변수이며, const는 데이터 값의 수정이 불가능한 상수이다. 둘 다 데이터 값에 이름을 지정하여 사용하고 싶고 데이터 값을 반복해서 사용하기 위해서 사용한다.


    // 변수 초기화는 변수 let만 가능하며 상수 const는 불가능하다
    let value; // (O) 가능
    const value; // (X) 불가

    // 변수 name에 '코딩'을 대입
    let name = '코딩';
    name = '코딩00'; // 다른 값 대입이 가능

    // 상수 name에 '코딩'을 대입
    const name = '코딩';
    name = '코딩00'; // 값 변경 불가능 => 코드 에러 발생

숫자 타입 변수 간에 계산이 가능하며, 문자열 타입 변수 간 결합이 가능하다.

    // 콤마(,)로 구분하면 한꺼번에 변수와 상수 선언 가능
    let a = 1, b = 2;
    const a = 1, b = 2;

    // 숫자 계산, 문자열 결합은 둘다 가능
    let number1 = 100;
    let number2 = 200;
    let sum = number1 + number2;
    console.log(sum); // 결과 : 300
    // console.log는 브라우저의 개발자 도구 콘솔에 결과를 보여주는 역할을 한다

    let name = '코딩';
    let birth = '00';
    let nickname = name + birth;
    console.log(nickname); // 결과 : '코딩00'

    // 변수 let과 마찬가지로 상수 const도 위와 동일하다
    const number1 = 100;
    const number2 = 200;
    const sum = number1 + number2;
    console.log(sum); // 결과 : 300

    const name = '코딩';
    const birth = '00';
    const nickname = name + birth;
    console.log(nickname); // 결과 : '코딩00'

but, 상수로 선언된 배열과 객체 내부의 값은 변경이 가능하다.

    const array = ['피카츄', '라이츄', '파이리'];
    array[2] = '꼬부기';
    // 결과 array = ['피카츄', '라이츄', '꼬부기'];

    const object = { nickname: '코딩', age: 24 };
    object.age = 34;
    // 객체 내부의 age값이 34으로 변경된다

값 변경이 필요한 데이터에만 let을 쓰고, 이외에는 const를 주로 이용하는 추세인데

const를 적극 이용함으로써 변경이 필요한 데이터와 그렇지 않은 데이터의 구분이 쉬워져 가독성이 높아지는 메리트를 얻게된다.

# 연산자

### 비교 연산자(두 개의 값 비교)
|구문|의미|
|:------:|:---:|
|`A == B`|A, B의 **값**이 같은가|
|`A === B`|	A, B의 값과 **데이터 타입**이 같은가|
|`A != B`|	A, B의 **값**이 다른가|
|`A !== B`|A, B의 값과 **데이터 타입**이 다른가|
|`A < B`|A가 B보다 작은가|
|`A <= B`|A가 B보다 작거나 같은가|
|`A > B`|A가 B보다 큰가|
|`A >= B`|A가 B보다 크거나 같은가|

***참고) 숫자와 문자열 등의 타입들이 서로 다른 타입일 경우 ==,!= 는 동일한 타입으로 간주하지만, ===, !== 는 다른 타입으로 간주한다.***

### 대입 연산자(복합형 대입 연산자 : 좌변과 우변의 연산 결과를 좌변의 변수에 대입하는 것)
|구문|의미|
|:------:|:---:|
|`x = y`|x = y (대입)|
|`x += y`|x = x + y (더하기)|
|`x -= y`|x = x - y (뺄셈)|
|`x *= y`|x = x * y (곱셈)|
|`x **= y`|x = x ** y (제곱)|
|`x /= y`|x = x / y (나눗셈)|
|`x %= y`|x = x % y (나머지)|


# 함수
함수란 처리 작업을 하나로 모아 이름을 지정하여 작업을 반복하여 사용하고 싶을 때 사용한다.

    // 함수 기본구조
    function 함수명(파라미터) {
        처리내용
        return 값;
    }
    // 함수 실행
    함수명();

    // 예시
    function ianFunction(a) {
        const result = a + 2;
        return result;
    }
    const ianResult = ianFunction(1);
    consoloe.log(ianResult); // 결과 : 3

---

    // 파라미터 개수는 제한이 없으며 콤마(,)로 구분한다
    function taxFunction(price, tax){
        const result = price + price * tax;
        return result; // 결과 반환값은 return으로 처리
    }

    // 함수를 실행하고 반환값을 myTax에 대입
    const myTax = taxFunction(100, 0.1);
    console.log(myTax); // 결과: 110

    // 파라미터가 없는 함수도 있다 => 함수 실행 시 ()에 아무것도 입력하지 않는다
    function ianFunction() {
        console.log('반가워요');
        return 100; // 반환값 없는 경우에 자체 생략 가능
    }
    ianFunction(); // 결과: 반가워요

    // return 구문으로 함수가 종료된다
    function ianFunction(){
        return 100;
        
        // return으로 함수 종료되서 아래는 실행 안됨
        console.log('안녕하세요');
    }

    // 하나의 함수 내에서 return 구문 몇 번이라도 사용 가능
    function ianFunction(a, b){
        // a가 100 이상이면 a 반환
        if (a >= 100) {
            return a;
        }
        // a가 100 미만이라면 b 반환
        return b;
    }

### 화살표 함수(Arrow Function)
함수를 간략히 기술하고 싶거나 this로 묶고 싶을 때 화살표 함수를 사용한다.

    // 화살표 함수 기본 구조
    const numberSum = (a, b, c) => {
        const result = a + b + c;
        return result;
    };

    // 함수의 실행 방식은 일반 함수와 동일
    numberSum(1, 2, 3); // 결과: 6

    // 화살표 함수는 일반 함수와 달리 파라미터가 하나인 경우는 () 생략 가능
    // 파라미터가 없거나 2개 이상인 경우는 () 생략 불가능
    const ianFunction1 = (a) => {
        return a + 1;
    };
    const ianFunction2 = a => {
        return a + 1;
    };

    // 화살표 함수의 정의가 한 줄인 경우 {}와 return 생략 가능
    const ianFunction3 = (a) => a + 2;

### 함수의 파라미터 초기값 설정
초기값이 설정된 파라미터는 값을 전달받지 않으면 '디폴트 파라미터(Default Parameter)' 를 사용한다.

    function taxFunction(price, tax = 0.1){ // 파라미터 = 초깃값 설정
	const result = price + price * tax;
    return result;
    }
    // tax의 인수 생략하면 초깃값 0.1이 사용된다
    const result1 = taxFunction(100);
    console.log(result1); // 결과: 110
    // tax의 전달 값 지정하면 해당 값 사용된다
    const result2 = taxFunction(100, 0.13);
    console.log(result2); // 결과: 113

### 다수의 파라미터를 가지는 함수
임의의 파라미터를 가지는 함수를 정의하고 싶을 때 '...파라미터' 를 이용한다.

        function numberSum(...prices){ // 임의의 다수 파라미터
        let result = 0;
        for (const value of prices) {
            result += value;
        }
    }
    const result1 = numberSum(1, 2);
    console.log(result1); // 결과: 3
    const result2 = numberSum(1, 2, 3, 4, 5);
    console.log(result2); // 결과: 15

# 조건문
### if 조건문
자바스크립트는 `if, else if, else` 를 사용하여 조건에 따른 처리가 가능하다. 당연히 `if` 단독으로도 사용 가능하며, `else if` 를 생략한 `if~else` 절도 가능하다.

    const coding = 29;

    if (coding >= 30) {
        alert('coding은 30 이상입니다.');
    } else if (coding >= 20) {
        alert('coding은 20 이상 30 미만입니다.');
    } else {
        alert('coding은 20 미만입니다.');
    }
    // 결과 : coding은 29이므로 else if의 조건에 해당된다.

---
    // if 단독
    if (true) {
        alert('Hello');
    }

    // else if 생략 (조건이 두가지로 나뉠 경우)
    const randomNum = Math.random() * 10;
    if (randomNum >= 5){
        alert('randomNum는 5 이상');
    } else {
        alert('randomNum는 5 미만');
    }

    // 처리 내용이 한 줄이라면 {} 생략도 가능
    const randomNum = Math.random() * 10;
    if (randomNum >= 5) alert('randomNum는 5 이상');

### switch 조건문
`switch` 문은 `case값`이 조건식에 만족 시 처리되며 만족되는 조건이 하나도 없는 경우 default 값으로 처리된다. `break` 는 처리를 종료하는 명령문이다.

    const ShMBTI = 'INFJ';

    switch (ShMBTI) {
	case 'INFJ':
    	alert('INFJ입니다.');
        break; // break생략시 끝나지 않고
               // 다음 case문의 조건 일치여부를 계속해서 확인한다
	case 'INTJ':
    	alert('INTJ입니다.');
    	break;
    default: // default는 어느 case도 실행되지 않았을 때
	     // 실행되는 영역으로 생략이 가능하다
    	alert('기타 MBTI입니다.');
        break;
    }
    //결과 : ShMBTI 는 'INFJ' 이므로 case 'INFJ'에서 조건 충족 후 break 에 의해 조건문이 종료됩니다.

# 반복문
### for 반복문
`for`문은 반복 작업을 처리하며, 대량의 데이터를 처리하거나 배열을 다룰 때 유용하다. `for(초기화; 반복문 조건; 반복 중 처리 구문;){반복처리내용}` 구문으로 사용한다.

    for (let i = 0; i < 10; i++) {
	console.log(i);
    }
    //결과 : 0~9까지 순서대로 출력

### while 반복문
`while`문은 조건을 만족하면 계속 반복 작업을 처리하며 `for`문과 유사하나 반복 조건만을 지정한다. 그러므로 코드를 통해 반복의 종료 시점을 지정해야 한다. `while(반복조건){반복처리내용}` 구문으로 사용한다.

    let i = 0;
    while (i < 5) {
        console.log(i);
        i += 1;
    }
    //결과 : 0~4까지 순서대로 출력

### continue문
반복문 `for문과 while문`의 반복 처리 작업 중 예외가 필요할 때 사용한다. `continue`문을 사용하면 해당 루프의 작업을 실행하지 않고 다음 루프로 넘어간다.

    for (let i = 0; i < 10; i++) {
	if (i % 2 === 0) { // i를 2로 나누었을 때 0이면 짝수에 해당한다
        continue; // i가 짝수인 경우 실행되지 않고 루프가 넘어간다
    }
    console.log(i); // 홀수만 출력된다
    }
    console.log('루프 종료'); // 루프가 끝나면 실행된다

    //결과 : 홀수 출력 후 루프 종료 출력


출처 : 이안의 평일코딩(https://iancoding.tistory.com/131)