# 2장. 변수(Variables)

## 2_1. 변수 선언 방법

Dart에서 변수를 선언하는 방법은 두 가지가 있다. 

### 2_1_1. Var Keyword

```dart
void main() {
	var name = 'Junhyung';
// name = 1;  에러_String 타입 아닌 int 타입
}
```

`var` 뒤에 변수명을 입력하여 선언

`var`로 선언했다는 것은 나중에 해당 데이터를 변경할 수 있다는 뜻이지만, **항상 같은 데이터타입으로만 바꿔줄 수 있다.**

관습적으로 **함수나 메서드 내부에 지역변수를 사용할 때 `var` 사용한다.**

### 2_1_2. DataType 지정

```dart
void main() {
	String name = 'Junhyung';
	name = 'DevJun'; // 가능
	// name = True; 에러
}
```

명시적으로 변수의 타입을 지정하여 변수를 선언

**Class에서 변수나 property를 선언할 때** 명시적으로 타입을 지정해서 선언한다.

### 2_1_3. Dynamic Type

```dart
void main() {
	var name; // dynamic name;와 동일
	name = 'Junhyung'; //String
	name = 12; //int
	name = true; //boolean

}
```

여러가지 타입을 가질 수 있는 변수에 쓰이는 키워드

변수 초기화 없이 선언만 하거나, `dynamic`라는 키워드로 명시하여 선언할 수 있음

> dynamic은 **Dart에서 권장하지 않는 데이터 타입**임
**필요할 때에만 사용할 것!**
> 

## 2_2. Nullable variables

### 2_2_1. null safety란?

null safety란, **개발자가 null값을 참조하지 못하게 함으로써 런타임 에러를 방지하는 것.** 

특정 데이터나 변수가 null이 될 수 있음을 명시하는 것.

기본적으로 모든 변수는 `non-nullable variables`. 즉, null값이 될 수 없는 변수들이다. 따라서 이를 nullable 변수로 만들어 줄 수 있는 것이 null safety.

```dart
//without null safety:
bool isEmpty(String string) => string.length == 0;

main() {
	isEmpty(null);  //RunTimeError 발생.(NoSuchMethodError)
}
```

위 코드에서는 String 타입을 인자로 받는 메서드에 null을 보내서 NoSuchMethodError 발생.

💡 그렇다면 이 null값을 삭제하면 해결되는 것 아닌가?


> 그렇지 않다. 
null은 부재, 즉 아무것도 있지 않음을 의미
따라서 프로그래밍상에서 유용할 때가 있음
> 

⇒ null safety로 이러한 에러 방지!!

### 2_2_2. null safety 사용법

by`?`

```dart
void main() {
	String? name = 'Junhyung';
	name = null // 정상 작동. name 은 String일 수도, null일 수도 있음.
}
```

## 2_3. Final Variables

앞서 살펴봤던 var, dataType을 이용해 선언한 변수는 (동일한 데이터 타입이라는 가정 하에) 나중에 값을 수정할 수 있는 변수들이다. 

그러나, **한 번 정의된 변수를 수정할 수 없게 만들고 싶을 때** 사용하는 것이 `Final Variables`.

javaScript, typeScript의 `const`와 동일한 기능

```dart
void main() {
	final String name = 'Junhyung';  //데이터타입 String은 안넣어줘도 됨.
	// name = 'DevJun'  에러_ 수정불가
}
```

## 2_4. Late Variables

초기 데이터 없이 변수를 선언할 수 있게 해줌

```dart
void main() {
	late final String name;
	// do something
	print(name); //name에 할당된 값 없어서 값을 넣기 전에는 접근할 수 없음
	name = '--';
	print(name); //name에 할당된 값 출력
}
```

변수를 먼저 만들고, 해당 데이터를 나중에 넣을 수 있게 해줌

실수를 방지해준다는 면에서 좋음

**API에서 얻어온 값을 써야 할 때** 유용하게 쓰임

## 2_5. Const Variables

complie-time constant를 만들어줌.

**javaScript, typeScript의 `const`와는 다름!**
(JS,TS의 const는 Dart의 final과 비슷함)

```dart
void main() {
	const API = '121212';
}
```

컴파일될 때 이미 값을 알고 있어야함. 즉, 앱스토어에 앱을 올리기 전에 알고 있는 값

(api를 통해 값을 가져오거나 사용자가 직접 값을 입력해야 하는 상황에서는 `const`가 아닌, `var`, `final`등을 사용)

---