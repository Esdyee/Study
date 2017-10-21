# 자료형과 변수

* 프로그래밍은 변수를 통해 값을 저장하고 참조함
* 연산자로 값을 연산 및 평가함
* 조건문과 반복문에 의해 흐름제어
* 함수로 재사용
* 객체, 배열 등으로 자료를 구조화

## 변수

* 변수는 위치를 기억하는 저장소
* 위치란 메모리 상의 주소(address)를 의미.
* 메모리 주소에 접근하기 위해 사람이 애하할 수 있는 언어로 지정한 식별자
* 값의 종류를 자료형(Data Type)이라고 한다.

## 자료형

* 기본 자료형(primitive data type)
	* Boolean
	* null
	* undefined
	* Number
	* String
	* Symbol
* 객체형
	* object

## 변수 호이스팅

* 모든 선언문은 호이스팅(Hoisting) 된다.
	* 호이스팅이란, var 선언문이나 function 선언문을 해당 Scope의 선두로 옮기는 것을 말										한다.
	* 자바스크립트는 var 선언문과 function 선언문을 해당 스코프의 맨위로 옮긴다.
		1. 선언 단계
		변수 객체에 변수를 등록한다. 이 변수 객체는 스코프가 참조하는 대상이 된다.
		2. 초기화 단계
		변수 객체에 등록된 변수를 메모리에 할당한다. 변수는 undefined로 초기화 된다.
		3. 할당 단계
		undefined로 초기화 된 변수에 실제 값을 할당한다.



# 연산자

## 산술 연산자
 * + , - , * , /
 * % , ++ , -- 

## 대입 연산자

* =, +=, -=, *=, /=, %=

## 비교 연산자

* == : 동등비교
* === : 일치비교
* != : 부등비교
* !== : 불일치비교
* > < >= <= : 관계비교
* ? :  삼항연산자 
	* 조건 ? 조건 true일 때 값 : 조건 false일 때 값

```
var condition = true;
var result = condition ? 'true' : 'false';
```

## 논리 연산자
* || : or
* && : and
* ! : not

## 단축 평가
* 논리연산자가 Boolean 값과 함꼐 사용되지 않을 경우 Boolean 값을 반환하지 않을 수 있다.
* Boolean 값으로 평가하기 위해 참조하여야 할 곳까지 진행한 후 평가를 중지하게 된 값을 반환한다.

## 타입 연산자

* typeof : 변수의 자료형을 문자열로 반환
* instanceof : 객체가 동일 객체형이 인스턴스이면 true


## !!
* !! 연산자의 역할은 피연산자를 불린값으로 변환하는 것




# 제어문

* 제어문(Control flow statement)은 조건문이나 반복문이 필요할 때 사용

## 블록 구문(Block statement)

* 구문들의 집합으로 가장 기본이 되는 구문
	* (블록은 중괄호로 그 범위를 정함)
* 블록 구문은 일반적으로 함수, 객체리터럴, 흐름 제어 구문에서 사용됨.

## 조건문

* 주어진 조건식(condition expression)이 참인지 거짓인지에 따라 실행되어질 구문들의 집함.
* if else문, switch 제공

### if문

```
if (조건식){

} else if(조건식) {
	
} else {

}
```

### switch 문

* switch 변수의 값과 일치되는 case문으로 실행 순서가 이동
* 일치되는 case가 없으면 default로 이동
* break 문이 없으면 case문의 조건과 일치 하지 않더라도 실행 순서는 다음 case 문으로 이동한다.





## 반복 문
* for, while, do while 제공

### for문
* 특정 조건이 거짓으로 판별 될 때까지 반복하는 구문


```

for ( [초기문]; [조건문]; [증감문){
	구문;
}

```

### while 문

### do while 문
* while문과 비슷하나 조건문을 확인하기 전에 무조건 1회는 실행함

### continue
* break 문은 반복문을 완전히 탈출한다.
* continue는 해당 조건의 실행을 Skip하고 반복문의 다음 조건으로 이동한다.




## 평가

* 조건식은 표현식의 일종
* 흐름제어를 위해서는 조건식을 평가하여 참/거짓을 구별 후 의사결정하는 것이 일반적

### 암묵적 강제 형 변환

### type conversion table

### data type conversion

### truthy & Falsy values

### checking equality

### checking existence