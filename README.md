# Flutter

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
