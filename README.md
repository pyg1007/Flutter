# Dart 문법

## 변수와 자료형
- 변할 수 있는 값

```Dart
void main(){
  String name = '아'; // name에 "아"라는 문자열을 할당
  int age = 20; // age에 20이라는 정수를 할당
  var name2 = '어'; // 타입추론 단, 한번 타입이 결정되면 다른타입으로 변경이 불가능
  name2 = 10; // Error
  bool isChecked = false; // true, false의 논리를 정할 때 사용
  double tall = 170.2;
  dynamic car = 'benz'; // 타입추론 var와는 다른점은 다른타입으로 변경이 가능
  car = 10;
}
```

## Null Safety
- 변수가 Null이 될 수 있는지를 명시적으로 지정할 수 있다.

```Dart
void main(){
  String name = '아'; // Not Null
  String name2 = null; // Error
  String? name2 = null; // Nullable
  ///name2 = '어';
  ///print(name2.length);
  print(name2?.length);
}
```

## Null 합류 연산자(??)
```Dart
void main(){
  String? name = null;
  String name2 = '아';
  String name3 = name ?? name2;
}
```
## late Keyward
- 늦은 초기화,

```Dart
late String name;
String? name2;
void main(){
  name = '아';
  name2 = '아';
}
```

위의 코드는 동일하게 사용할수 있어보이지만, 차이점은 late 키워드가 붙는다면 언젠가는 초기화 해준다는 의미. name2는 초기화를 해주지 않아도 됨.

## const vs final
- 상수
  - 항상 같은 값

- final
  - 최초에 값이 한번 할당되면 다시 할당할 수 없음.
```Dart
void main(){
  final int testValue = 10;
  testValue = 20; // Error
  final int testValue2;
  testValue2 = 10;
}
```
- const
  - 최초에 값이 한번 할당되면 다시 할당할 수 없음. 단, 선언과 동시에 할당해야 함.
  - 해당값은 컴파일 단계에서 확정되어야 함
```Dart
void main(){
  const int testValue = 10;
  testValue = 20; //Error
  const int testValue2; // null
  testValue2 = 20;// Error
}
```

## 연산자와 표현식
- 산술연산자
```Dart
void main(){
  int a = 10;
  int b = 3;
  int plus = a + b;
  int minus = a - b;
  int product = a * b;
  double divide = a / b;
  int remain = a % b;
  int mok = a ~/ b;
}
```

- 비교연산자
```Dart
void main(){
  bool isResult = (a==b);
}
```

- 논리연산자
```Dart
void main(){
  bool disjunction = (true || false); // 논리 합(OR)
  bool conjunction = (true && false); // 논리 곱(AND)
  bool logicalNot = !conjunction; // 논리 부정(NOT)
} 
```

- 할당연산자
```Dart
void main(){
  double c = 10;
  c += 30;
  c -= 30;
  c *= 30;
  c /= 30;
}
```

- 조건연산자
```Dart
void main(){
  int age = 20;
  String ageStatus = age >= 18 ? '성인' : '미성년자'; // 삼항연산자
}
```
  
## 조건문과 반복문
- if - else문
```Dart
void main(){
  int age = 20;
  if(age >= 18){
    print('성인입니다.');
  }else{
    print('미성년자입니다.');
  }
```

- switch문
```Dart
void main(){
  String grade = 'A'
  switch(grade){
    case 'A':
      print('우수);
      break;
    case 'B':
      print('보통 등급');
      break;
    case 'C':
      print('부족 등급');
      break;
    default:
      print('매우 부족 등급');
      break;
  }
}
```

- for 반복문
일정한 범위에서 반복 작업을 수행할 때 사용
```Dart
void main(){
  for(int i = 0; i < 5; i++){ // ++ : 증감연산자
    print('$i번 반복합니다.'); // String interpollation
  }
}
```

- while 반복문
조건이 참인 경우 반복 작업을 수행할 때 사용
```Dart
void main(){
  int count = 0;
  while(count <3){
    count++;
    print('$count번 반복합니다.');
    // break; - 탈출 구문, 바로 탈출가능함.
  }

}
```

# List & Map
- List
    - 순서가 있는 데이터 컬렉션, 인덱스(index)로 접근 가능
```Dart
void main(){
  List<int> numbers = [];
  List<int> numbers1 = [1,2,3,4,5];

  //데이터 추가
  numbers1.add(6);

  //List 데이터 읽기
  for(int i = 0; i<number1.length; i++){
    print('$i번째데이터는 ${number1[i]}입니다.');
  }

  //데이터 삭제(index를 이용하여 특정위치에 있는 데이터를 삭제)
  numbers1.removeAt(0);
}
```

- Map
  - Key 와 Value의 한쌍으로 이루어진 데이터 컬렉션, 각 Key는 고유하며, Key를 이용하여 Value데이터 접근 가능
```Dart
void main(){
  Map<String, int> scoreMap = {};
  Map<String, int> scoreMap1 = {'홍길동':100, '아무개':50};

  //데이터 접근
  print(scoreMap1['홍길동']);

  //데이터 갱신
  scoreMap1['홍길동'] = 88;

  //데이터 추가
  scoreMap1['최아무개'] = 50;

  //데이터 조회
  scoreMap1.forEach((key, value){
    print('$key는 $value점 입니다.')
  });
}
```

# 함수와 메서드
- 함수
  - 코드의 논리를 분리하고 재 사용성을 높이는데 사용
  - 함수 이름, 매개변수(parameter), 반환유형(return type)으로 구성
```Dart
void main(){ // 프로그램의 출발지점인 메인 함수, void 리턴타입일 경우 아무런 값을 반환하지 않고 실행만 함.
  print(add(3,5)); // 함수 실행
}

// 파라미터 a, b를 입력받아 int형으로 리턴해주는 함수
int add(int a, int b){
  return a + b;
}
```

- 메서드(Method)
  - class 내부에서 정의된 함수
```Dart
class UserInfo{
  String name;
  int age
  void setUserInfo(){
  
  }
}
```

# Positional Parameter & Named Parameter
```Dart
void setStart1(String name, int age){ // Positional Parameter
}
void setStart2({String name = '홍길동', int age = 24}){ // Named Parameter(선택적 파라미터)
}
void setStart3({required String name}){ // Named Parameter(필수적 파라미터)
}
void main(){
  setStart1('홍길동', 30);
  setStart2(age: 50);
  setStart2(name : '아무개');
  setStart2();
  setStart3(name: '홍길동');
}
```

# Class 와 상속
- Class
  - 객체를 생성하기 위한 템플릿 또는 청사진, 설계도
 
- 상속
  - 기존 클래스의 특성을 다른 클래스에서 재사용하고 확장하는 매커니즘
  - 부모 클래스(super class)와 자식 클래스(sub class)간의 상속관계

```Dart
class Person{
  String name;
  int age;

  //생성자 (constructor)
  Person(this.name, this.age);

  void say(){
    print('저는 $name이고 $age살 입니다.')
  }
}

class Man extends Person{
  Man(String name, int age) : super(name, age);

  @override
  void say(){
    super.say();
    print('\n은 남자입니다.');
  }
}

void main(){
  Person person = Person('홍길동', 15); // 클래스 인스턴스 생성
  person.say();

  Man man = Man('아무개', 20);
  man.say();
}
```

#생성자(constructor)와 선택적 매개 변수
- 생성자(constructor)
  - 클래스의 인스턴스를 초기화하는 특별한 메서드
  - 클래스를 생성할 때 가장 먼저 호출 되는 자
```Dart
class Person{
  //기본 생성자 (default constructor), 생략할 수 있음.
  Person();
}
class Person2{
  String name;
  int age;
  //매개변수가 존재하는 생성자
  Person2(this.name, this.age);
}

class Person3 {
  String name;
  int age;
  Person3({required this.name, required this.age});
}
void main(){

  var person = Person();
  var person2 = Person2('아무개', 30);
  var person3 = Person3('아무개', 30);

}
```

# Enum타입
- 열거형, 타입 정의 보통 많이 사용, 상수들의 그룹을 정의할 때 유용함.
- 협업하는 개발자들 간에 코드를 더 읽기 쉽고 이해하기 쉽게 만들어 줄 수 있기 때문에 사용함.

```Dart
enum Color {
  red,
  green,
  blue,
  yellow,
}

void main(){
  Color myColor = Color.red;

  //조건문으로 비교
  if(myColor == Color.red){
    print('빨간색');
  } else if(myColor == Color.green){
    print('초록색');
  } else if(myColor == Color.blue){
    print('파란색');
  } else{
    print('노란색');
  }

  //순서를 이용 가능
  for(int i = 0; i <= Color.values.length; i++){
    print(Color.values[i]);
  }
}
```

# Future & await 을 이용한 비동기
## 동기 vs 비동기
- 동기
  - 작업이 순차적으로 실행
- 비동기
  - 작업이 순차적으로 실행되지 않으며, 동시에 여러 작업을 처리
## Future
- 비동기 작업의 결과 또는 완료 상태를 나타내는 객체

## await
- 비동기 함수 내에서 사용되며, await 뒤에 나오는 결과 값이 완료될 때까지 실행을 일시적으로 중단.
```Dart
void main(){
  play
}
Future<void> playComputerGame() async{
  startBoot();
  await startInternet();
  startGame();
}
void startBoot(){
  print('1. boot completed');
}
await Future<void> startInternet() async{
  Future.delayed(Duration(seconds: 3), (){
    print('2. internet completed');
  });
  print('delay completed');
}

void startGame(){
  print('3. game completed');
}
```

# Column, Row, Expanded 위젯
## Column
- 세로로 위젯을 쌓아서 정렬하는 위젯

## Row
- 가로로 위젯을 쌓아서 정렬하는 위젯

### 속성(프로퍼티)
- mainAxisSize
  - min : 크기만큼만 차지
  - max : 남은 영역을 모두 사용
- mainAxisAlignment
  - start : 왼쪽 정렬
  - end : 오른쪽 정렬
  - center :가운데 정렬
  - spaceEvenly : 영역을 고르게 정렬
  - spaceBetween : start, end 사이에 고르게 배치
  - spaceAround : 앞/뒤 영역을 두고 배치

## Children
- 위젯의 하위로 다수의 위젯을 추가할 때 사용

## Expanded
- 비율적으로 배치하는 위젯
