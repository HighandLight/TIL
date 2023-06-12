# 3장. 데이터 타입(Data Type)

## 3_1. 기본적 데이터 타입

```dart
void main() {
	String name = 'junhyung'; // String
	bool dev = true; // Boolean
	int age = 24; // Integer
	double money = 99.99; // Double
	num x = 1;  //int or duble 둘 다 가능
	// x = 1.1;
}
```

→ 너무 쉬우니 생략.. 

## 3_2. List

```dart
void main() {
	var numbers = [1, 2, 3, 4];
	// List<Integer> numbers = [1, 2, 3, 4]; //와 동일
}
```

**Dart 에서의 List의 가장 큰 특징은 Collection If 와 Collection For을 지원한다는 점!**

### 3_2_1. Collection If

- If로 존재여부가 확실치 않은 요소를 List의 요소로 넣을 수 있음
    
    ```dart
    void main() {
    	var giveMeThree = true;
    	var numbers = [
    		1, 
    		2,
    		if(giveMeThree) 3, //giveMeThree가 true라면 리스트 안에 3 추가!
    	]; 
    }
    ```
    
    다음처럼 조건문 코드를 짤 필요 없이 한 줄이면 된다!
    
    ```dart
    if(giveMeThree){
    	numbers.add(3);
    }
    ```
    
    앱 내에서 메뉴나 navigation bar를 만드는데, User가 로그인을 했는지 안했는지를 나타내는 버튼을 추가하고 싶을 때,, 유용히 쓰임!!
    

### 3_2_2. String Interpolation `$`

```dart
void main() {
	var name = 'Junhyung';
	var greeting = 'Hello everyone, my name is $name, nice to meet you!';
}
```

- 변수가 이미 존재할 때 용이한 방식
- 그렇다면,, 계산을 실행해야 할 때는 어떻게 코드를 작성할까..?

```dart
void main() {
	var name = 'Junhyung';
	var age = 24;
	var greeting = 'Hello everyone, my name is $name, I\'m ${age +2} years old.';
}
```

### 3_2_3. Collection For

```dart
void main() {
	var oldFriends = ['J', 'H'];
	var newFriends = [
	'R', 
	'N',
	for(var friend in oldFriends) "❤️ ${friend}",
	];
}
```

## 3_3. Map

- Python에서 `dictionary`, JavaScript, TypeScript에서 `object`와 비슷한 개념

```dart
void main() {
	var player = {
		'name' : 'Junhyung',
		'xp' : 999.99,
		'super power' : true,
	}
}
```

player의 자료형을 var로 선언해주었는데,, key와 value의 자료형을 다음처럼 명시해줄 수 있다.

```dart
Map<String, object> player = {
```

Dart의 모든 클래스는 object 클래스를 상속받기에,, object는 기본적으로 어떤 자료형이든 될 수 있다.

(TypeScript의 `any`와 비슷한 개념)

Map을 이용해서 다음처럼 복잡한 자료형도 구현할 수 있음

```dart
void main() {
	List<Map<String, Object>> players = [
		{
			'name' : 'DevJun',
			'lv' : 99999;
		},
		{
			'name' : 'ArtistJun',
			'lv' : 1;
		},
	]
}
```

- Key, Value를 가지는 구조로 object를 만들 때, 그리고 그것들이 특정 형태를 가질 때는 Map이 아닌 Class를 추천함!!

## 3_4. Set

```dart
void main() {
	var numbers = {1, 2, 3, 4};  //타입 명시 : Set<int> numbers

	numbers.add(1);
	numbers.add(1);
	numbers.add(1);
	print(numbers);  //{1, 2, 3, 4)
}
```

- List와 달리 **모든 요소들이 유니크함!(중복 X)**
- Python의 `tuple`과 동일

---