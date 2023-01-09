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

```

# 8
```java

```

# 9
```java

```

# 10
```java

```

# 11
```java

```

# 12
```java

```

# 13
```java

```

# 13
```java

```

# 14
```java

```

# 15
```java

```

# 16
```java

```

# 17
```java

```

