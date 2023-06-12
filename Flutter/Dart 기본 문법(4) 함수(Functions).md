# 4장. 함수(Functions)

## 4_1. 함수 기본

```dart
void sayHello(String name) {
	print("Hello $name nice to meet you");
}

void main() {
	print(sayHello('Junhyung'));
}
```

`void` : (반환타입) 아무것도 return하지 않음 

### Fat Arrow Syntax

```dart
String sayHello(String name) {
	return "Hello $name nice to meet you";
}
```

이처럼 String값 리턴하는 함수를..

```dart
String sayHello(String name) => "Hello $name nice to meet you";
```

이처럼 한 줄로 표현할 수 있음.

단, **한줄짜리의 간단한 코드일때만 Fat Arrow Syntax 사용할 수 있음!**

## 4_2 Named Parameters `{argument1, argument2, argument3, … }`

❗️if.. 함수가 받는 인자가 여러개일 경우, 인자들 사이의 순서를 일일이 기억해서 입력해줘야 하는 번거로움.(positional parameters)

→ 이 positional parameters의 문제점을 해결하기 위해 **순서에 관계없이** 인자들을 입력해줄 수 있는게 Named Parameters!!

// Positional Parameters

```dart
void sayHello(String name, int age, String country) {
	return "Hello $name, you are $age, and you come from $country.";

void main() {
	print(sayHello('Junhyung', 19, 'korea'));
}
```

이처럼 main함수에서 sayHello함수 호출 시, 인자들 순서 고려해서 입력해줬던 코드를 

```dart
void sayHello({String name, int age, String country}) {
	return "Hello $name, you are $age, and you come from $country.";

void main() {
	print(sayHello(
		age : 24,
		country : 'korea',
		name : 'Junhyung'));
}
```

이처럼 인자 순서들 관계 없이 호출해줄 수 있다는 장점!

❓ 하지만,, 만약 사용자가 sayHello()인자 세가지 중 **작성 안한 것이 있다면,,??**

⇒ Dart의 null safety 작동!!


-이에 대한 해결 방법은 두가지.

**Sol 1) 함수 선언시, 인자의 default 값 설정**

```dart
void sayHello({
	String name = 'Junhyung', 
	int age = 24, 
	String country = 'korea'}) {
	return "Hello $name, you are $age, and you come from $country.";
```

→ 호출시 특정 인자값 입력 안해도 미리 지정해둔 default값으로 자동 입력!

**Sol 2) Requier Modifier 이용**

```dart
void sayHello({
	required String name, 
	required int age,
	required String country}) {
	return "Hello $name, you are $age, and you come from $country.";
```

→ named parameter가 사실은 required임을 명시해줌으로써 필수 값으로 만들어줌!

## 4_3. Optional Positional Parameters `[ ? ]`

❗️다수의 인자 중, 특정 인자는 안받아도 되는 경우,, 

→ Optional Positional Parameters 사용!!

```dart
void sayHello({String name, int age, [String? country = 'korea']}) 
	=> "Hello $name, you are $age, and you come from $country.";

void main() {
	sayHello('JunhyungJ',24);  //컴파일 성공!
}
```

→ `?` : 해당 인자가 null일수도, 아닐수도 있음을 명시 (not required)

→ country 인자는 not required인자이고, default값이 ‘korea’인 인자!!

💡 ? 그냥 country값에만 default값 부여해주면 되는 것 아닌가?

❗ Nico도 잘 사용은 안하는 Parameters..알아만 보고 넘어갈것.


## 4_4. QQ Operator ??

```dart
String capitalizeName(String name) => name.toupperCase(); 

void main() {
	capitalizeName('Junhyung'); // JUNHYUNG
}
```

❗ 그렇다면, name에 null값이 들어갈 수 있도록 하고 싶다면,,?


```dart
String capitalizeName(String? name) => name.toUpperCase(); //error
```

error. 

null값은 toUpperCase()메서드 호출할 수 없기에,, 

→ 조건문을 통해 구현해줘야 함!

```dart
String capitalizeName(String? name) {
	if (name != null) {
		return name.toUpperCase();
	}
	return 'JUNHYUNG'
}
```

이 조건문을 다음과 같이 삼항연산자로 한줄로 줄일 수 있고, 

```dart
String capitalizeName(String? name) => name != null ? name.toUpperCase() : 'JUNHYUNG';
```

이 조건문을 다시 QQ Operator를 통해 간단히 표현할 수 있다. 

```dart
String capitalizeName(String? name) => name?.toUpperCase() ?? 'JUNHYUNG';
```

> left ?? right
left가 null이라면, 자동으로 right 리턴!
(name 뒤의 ?는 name자체가 null인 경우에 toUpperCase()호출할 수 없기에
> 

### QQ equal

```dart
void main(){
	String? name;
    // 만약 name이 null인 경우 할당한다.
    name ??= 'jisoung';
}
```

## 4_5. Typedef

: 자료형이 헷갈릴 때 도움이 될 alias를 만드는 방법

typedef를 이용하면 자료형을 간편하게 작성할 수 있다.

다음의 코드를 typedef를 사용해서 간편하게 작성할 수 있다.

```dart
//Before
List<int> reverseListOfNumbers(List<int> list) {
	var reversed = list.reversed;
    return reversed.toList();
}
```

```dart
//After
typedef ListOfInts = List<int>;

ListOfInts reverseListOfNumbers(ListOfInts list) {
	var reversed = list.reversed;
    return reversed.toList();
}
```