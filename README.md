# Flutter

## 변수와 자료형
- 변할 수 있는 값

```Dart
String name = '아'; // name에 "아"라는 문자열을 할당
int age = 20; // age에 20이라는 정수를 할당
var name2 = '어'; // 타입추론 단, 한번 타입이 결정되면 다른타입으로 변경이 불가능
name2 = 10; // Error
bool isChecked = false; // true, false의 논리를 정할 때 사용
double tall = 170.2;
dynamic car = 'benz'; // 타입추론 var와는 다른점은 다른타입으로 변경이 가능
car = 10;
```

## Null Safety
- 변수가 Null이 될 수 있는지를 명시적으로 지정할 수 있다.

```Dart
String name = '아'; // Not Null
String name2 = null; // Error
String? name2 = null; // Nullable
///name2 = '어';
///print(name2.length);
print(name2?.length);
```

## Null 합류 연산자(??)
```Dart
String? name = null;
String name2 = '아';
String name3 = name ?? name2;
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
