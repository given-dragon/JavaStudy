# 1
```java
// a
(String name, int i) -> {
    System.out.println(name+"="+i);
}

// b
(int a) ->  x * x 

// c
() -> { return (int) (Math.random() * 6);}

// d
(int[] arr) -> {
    int sum=0;
    for(inti : arr)
        sum += i;
    return sum;
}

// e
() -> new int[]{}
```

# 2
```java
String::length()
int::new
Arrays::stream
String::equals
Integer::compare
Card::new
System.out::println
Math::random
String::toUpperCase
NullPointerException::new
Optional::get
StringBuffer::append
System.out::println
```

# 3
```java
IntBinaryOperator
```

# 4
```java
public static void main(String[] args) {
    Stream<Integer> die = IntStream.rangeClosed(1, 6).boxed();

    die.flatMap(i -> Stream.of(1,2,3,4,5,6).map(j -> new int[] {i, j}))
            .filter(arr -> arr[0] + arr[1] == 6)
            .forEach(arr -> System.out.println(Arrays.toString(arr)));

}
```

# 5
```java
public static void main(String[] args) {
    String[] strArr = {"aaa", "bb", "c", "dddd"};
    
    IntStream lenStream = Arrays.stream(strArr).mapToInt(String::length);
    
    System.out.println("sum = " + lenStream.sum());
}
```

# 6
```java
public static void main(String[] args) {
    String[] strArr = {"aaa", "bb", "c", "dddd"};
    IntStream lenStream = Arrays.stream(strArr).mapToInt(String::length);
    System.out.println("sum = " + lenStream.max().getAsInt());
}
```

# 7
```java
public static void main(String[] args) {
    new Random().ints(1, 46)
            .distinct() // 중복 제거
            .limit(6)   // 6개로 제한
            .sorted()   // 정렬
            .forEach(System.out::println);
}
```

# 8
```java
Map<Boolean, Map<Boolean, Long>> failedStuBySex =
        Stream.of(stuArr)
        .collect(
        partitioningBy( // 성별 구분
                Student::isMale,
                partitioningBy(s -> s.getScore() > 150, counting()) // 성적 구분
        )
);
```

# 9
```java
Map<Integer, Map<Integer, Long>> totalScoreByHakAndBan =
        Stream.of(stuArr).collect(
                groupingBy(
                        Student::getHak,    // 학년별 그룹화
                        groupingBy(
                                Student::getBan,
                                summingLong(Student::getScore)
                        )
                )
        );
```
