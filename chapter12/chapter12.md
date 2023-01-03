# 1
```java
a. Box<Object> b = new Box<String>(); 
b. Box<Object> b = (Object)new Box<String>();
c. new Box<String>().setItem(new Object());
```
- a -> 대입 타입이 다르다.
- b -> 인스턴스는 Object타입이고, 참조변수는 ```Box<Object>```타입이다.
- c -> 위 상황에서 setItem의 매개변수 타입은 String만 가능하다.


# 2
```java
c. Juicer.<Fruit>makeJuice(new FruitBox<Fruit>());
d. Juicer.makeJuice(new FruitBox<Apple>());
```
- c -> 제네릭 타입을 Fruit으로 설정하였으므로 올바르게 호출하였음.
- d -> 제네릭 타입을 생략한 형태이고, ```Juicer.<Apple>makeJuice(new FruitBox<Apple>());```와 같다고 볼수있다.

# 3
```java
c. Box<?> b = new Box<Object>();
d. Box<Object> b = new Box<Fruit>();
g. Box<? extends Object> b = new Box<? extends Fruit>();
```
- c -> ```<?> == <? extends Object>```이다. 다만 정의를 할 때 타입을 Fruit으로 제한해두어 Box의 생략된 타입은 Fruit이다. 따라서 Object는 Fruit의 자식이 아니기 때문에 잘못되었다.
- d -> Object과 Fruit은 타입이 같지 않다.
- g -> new 연산자는 타입을 정확히 명시해주어야 한다.

# 4
```java
public static <T extends Product> ArrayList<T> merge(
        ArrayList<T> list, ArrayList<T> list2) {
    
    ArrayList<T> newList = new ArrayList<>(list);
    newList.addAll(list2);
    return newList;
}
```

# 5
```java

```

# 6
- c. Native

# 7
```java
b. @TestInfo(1) class Exercise12_7 {}
d. @TestInfo("bbb", "ccc") class Exercise12_7 {}
```
- b -> 요소의 이름이 value가 아닌 경우에는 이름 생략 불가능. 해당 요소의 이름인 count를 사용하여 ```@TestInfo(count=1)```가 맞는 표현.
- d -> 요소의 타입이 배열이고 값이 여러개인 경우 다음과 같이 중괄호를 사용하여 묶어주어야 함. ```@TestInfo({"bbb", "ccc"}) || @TestInfo(value={"bbb", "ccc"})```
