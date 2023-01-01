# 1
```java
public static void main(String[] args){
    ArrayList list1 = new ArrayList();
    ArrayList list2 = new ArrayList();
    ArrayList kyo = new ArrayList(); // 교집합
    ArrayList cha = new ArrayList(); // 차집합
    ArrayList hap = new ArrayList(); // 합집합
    list1.add(1);
    list1.add(2);
    list1.add(3);
    list1.add(4);
    list2.add(3);
    list2.add(4);
    list2.add(5);
    list2.add(6);

    // 교집합
    kyo.addAll(list1);
    kyo.retainAll(list2);

    // 차집합
    cha.addAll(list1);
    cha.removeAll(list2);

    // 합집합
    hap.addAll(list1);
    hap.removeAll(kyo);
    hap.addAll(list2);

    System.out.println("list1="+list1);
    System.out.println("list2="+list2);
    System.out.println("kyo="+kyo);
    System.out.println("cha="+cha);
    System.out.println("hap="+hap);
}
```

# 2
- 7, 6, 3, 2 순서로 출력

# 3
- a. 첫 번째 요소 삭제
- 첫 요소를 삭제하면 나머지 배열 요소들을 모두 이동시켜야 하기 때문에.

# 4
- 중간에 있는 6번째 요소가 접근 시간이 가장 많이 걸린다.
- 리스트의 시작과 끝이 연결되어있어 중간 요소의 접근이 가장 오래 걸린다.

# 5
```java
class Student implements Comparable {
    String name;
    int ban;
    int no;
    int kor, eng, math;

    Student(String name, int ban, int no, int kor, int eng, int math) {
        this.name = name;
        this.ban = ban;
        this.no = no;
        this.kor = kor;
        this.eng = eng;
        this.math = math;
    }

    int getTotal() {
        return kor+eng+math;
    }

    float getAverage() {
        return (int) ((getTotal() / 3f)*1-+0.5)/10f;
    }

    public String toString() {
        return name + "," + ban + "," + no + "," + kor
                + "," + eng + "," + math
                + "," + getTotal() + "," + getAverage();
    }

    public int compareTo(Object obj) {
        if(obj instanceof Student)
            return name.compareTo(((Student) obj).name);
        return -1;
    }
}
```

# 6
```java

```

# 7
```java

```

# 8
```java

```
