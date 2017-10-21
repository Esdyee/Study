
# Immutable

## immutable value vs mutable value

* 기본 자료형은 immutable value
* 기본 자료형 이외의 값은 모두 Object 객체 -> mutable value

* Hello 값을 지우고 world를 할당하는게 아니다.
* Hello 값은 그대로 있고, world를 새로운 메모리에 할당하고, Hello의 참조를 끊는 것이다.
* 즉, Hello 값은 살아있다.

```
var str = 'Hello';
str = 'world';
```

* 2행에서 slice()메소드는 statement 변수에 저장된 문자열을 변경 X
* 새로운 문자열을 생성 -> 생성한 문자를 수정후 반환
* 메소드 같은 것을 사용할 때, 기존 변수에 담겨 있던 값을 변경하지 않기 위해 immutable value 적용.

```
var statement = 'I am an immutable value';
var otherStr = statement.slice(8,17);

```

* 객체인 arr은 push 메소드에 의해 update
* push 메소드의 리턴값은 arr의 length
* v2에는 arr 배열의 length 값이 들어있음.

```
var arr = [];
console.log(arr.length); // 0

var v2 = arr.push(2);    // arr.push()는 메소드 실행 후 arr의 length를 반환
console.log(arr.length); // 1
```


* user.name의 값을 myName에 할당할 때 string 타입으로 할당한다.
* myName은 string 타입이다.


```
var user = {
  name: 'Lee',
  address: {
    city: 'Seoul'
  }
};

var myName = user.name; // 변수 myName은 string 타입이다.

user.name = 'Kim';
console.log(myName); // Lee

myName = user.name;  // 재할당
console.log(myName); // Kim
```

* user2에 user1을 할당한다.
* user2는 user1을 복사한게 아니라, 참조하고 있으므로 user2 변경하면 user1도 같이 바뀜.


```
var user1 = {
  name: 'Lee',
  address: {
    city: 'Seoul'
  }
};

var user2 = user1; // 변수 user2는 객체 타입이다.

user2.name = 'Kim';

console.log(user1.name); // Kim
console.log(user2.name); // Kim
```

## 불변 데이터 패턴(immutable data pattern)

* 의도하지 않는 객체의 변경이 발생하는 원인
	* "레퍼런스를 참조한 다른 객체"에서 "객체"를 변경하기 떄문.
	* "객체"를 불변객체로 만들어 프로퍼티의 변경을 방지.
	* 이를 방어적 복사를 통해 새로운 객체를 생성한 후 변경


### Object.assign

* Object.assign은 타깃 객체로 소스 객체의 프로퍼티를 복사
* ES6에서 추가된 메소드이며 IE는 지원X
* 객체 프로퍼티를 완전복사함
* 객체 프로퍼티를 단순참조 X

* Object.assign( "copy 초기화 이후 생성할 내용" , "복사해서 넣을 객체(obj)")

```
var obj = {a:1};
var copy = Object.assign( {b:2} , obj);


```

* Object.assign으로 Merge하기

```
const o1 = {a: 1};
const o2 = {b: 2};
const o3 = {c: 3};

const merge1 = Object.assign(o1,o2,o3);


const o4 = {a:1};
const o5 = {b:2};
const o6 = {c:3};

const merge2 = Object.assign({}, o4, o5, o6);
```


### Object.freeze

* Object.freeze(객체);
* 객체를 참조해서 변경하지 못하게 얼려버림

```
const user1 = {
	name:'Lee'
}

Object.freeze(user1);
user1.name = 'Kim';

console.log(user1) //name이 Kimd으로 안바뀌고 Lee이다!

console.log(Object.isFrozen(user1)); //객체가 얼어붙었는지 확인할 수 있는 메서드(반환값은 Bool)
```

* 얼려붙어도 객체의 객체 안에 들은 값은 변경이 된다.

```
const user = {
  name: 'Lee',
  address: {
    city: 'Seoul'
  }
};

Object.freeze(user);

user.address.city = 'Busan'; // 변경된다!

```


### Immutable.js

* Object.assign과 Object.freeze는 불변 객체를 만드는 방법은 번거럽고 성능상 이슈가 존재함.
* 큰 객체에 사용 권장 X
* 대안으로 Immutable.js 사용