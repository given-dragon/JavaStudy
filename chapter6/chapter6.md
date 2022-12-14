# 1
```java
public class SutdaCard {
    int num;
    boolean isKwang;
}
```

# 2
```java
    int num;
    boolean isKwang;

    public SutdaCard( int num, boolean isKwang){
            this.num = num;
            this.isKwang = isKwang;
    }
    public SutdaCard() {
            this.num = (int) (Math.random() * 9) + 1;
            this.isKwang = num == 1 || num == 3 || num == 8;
    }
    
    public String info() {
            return num+ (isKwang ? "k" : "");
    }
```

# 3
```java
class Student {
    String name;
    int ban, no, kor, eng, math;
}
```
# 4
```java
class Student{
    String name;
    int ban, no, kor, eng, math;

    public int getTotal() {
        return  kor + eng + math;
    }

    public float getAverage() {
        float avg = (float)(kor + eng + math)/3;
        return (float)Math.round(avg*10)/10;
    }
}
```
# 5
```java
class Student {
    String name;
    int ban, no, kor, eng, math;

    public Student(String name, int ban, int no, int kor, int eng, int math) {
        this.name = name;
        this.ban = ban;
        this.no = no;
        this.kor = kor;
        this.eng = eng;
        this.math = math;
    }

    public int getTotal() {
        return kor + eng + math;
    }

    public float getAverage() {
        float avg = (float) (kor + eng + math) / 3;
        return (float) Math.round(avg * 10) / 10;
    }

    public String info() {
        return String.format("%s,%d,%d,%d,%d,%d,%d,%.1f\n", name, ban, no, kor, eng, math, getTotal(), getAverage());
    }
}
```

# 6
```java
static double getDistance(int x, int y, int x1, int y1) {
    return Math.sqrt(Math.pow(x1-x, 2) + Math.pow(y1-y, 2));
}
```

# 7
```java
public double getDistance(int x, int y) {
    return Math.sqrt(Math.pow(this.x-x, 2) + Math.pow(this.y-y, 2));
}
```

# 8
- 클래스 변수(static): width, height
- 인스턴스변수: kind, num
- 지역변수: k, n, card, args

# 9
모든 병사의 공격력과 방어력이 같아야 한다.
그러므로 weapon과 armor가 static으로 선언되어야 한다.
weaponUp과 armorUp은 static변수를 다루는 메서드이므로 역시 static으로 선언되야 한다.
- weapon, armor, weaponUp, armorUp

# 10
- b. 생성자는 객체를 생성 하기 위한 것. -> 초기화를 위해 
- e. 생성자는 오버로딩 할 수 없다. -> 오버로딩 가능


# 11
- b. 클래스 내에서라면 어디서든 사용할 수 있다. -> 클래스 맴버에는 사용 불가능.

# 12
- c. 리턴타입이 달라야 한다. -> 오버로딩에는 영향 안줌
- d. 매개변수의 이름이 달라야 한다. -> 오버로딩에는 영향 안줌

# 13
- ```java 
  b. long add(long a, long b) { return a+b;}
  ```
- ```java 
  c. int add(byte a, byte b) { return a+b;}
  ```
- ```java 
  d. int add(long a, int b) { return (int)(a+b);}
  ```
  
# 14
- c. 초기화 블럭보다 생성자가 먼저 수행된다. -> 초기화 수행 수 생성자 수행
- e. 클래스 변수보다 인스턴스 변수가 먼저 초기화된다. -> 클래스 변수는 컴파일 시점에 초기화

# 15
- a. 기본값-명시적초기화-초기화블럭-생성자

# 16
- a. 자동 초기화되므로 별도의 초기화가 필요없다. -> 자동초기화 되지 않으며 초기화 필요
- e. 힙(heap)영역에 생성되며 가비지 컬렉터에 의해 소멸된다. -> 호출스택에 생성됨

# 17
- b. println메서드를 제외한 나머지 메서드들은 모두 종료된 상태이다. -> 대기상태

# 18
- 라인 A: 클래스 변수 초기화에 인스턴스 변수를 사용했음.
- 라인 B: 클래스 메서드에서 인스턴스 변수를 출력함.
- 라인 D: 클래스 메서드에서 인스턴스 메서드를 사용함.

# 19
```
ABC123
After change: ABC123
```
1. change호출 시 str 주소 참소
2. 문자열을 붙이게 되면 새로운 지역변수 생성(주소 새로 생성)
3. change가 종료되면 가비지컬렉터에 의해 지역변수는 제거됨
4. 메인으로 돌아오면 str은 초기상태 그대로

# 20
```java
public static int[] shuffle(int[] arr) {
    for (int i=0; i<arr.length; i++) {
        int idx = (int) (Math.random() * arr.length);
        int temp = arr[i];
        arr[i] = arr[idx];
        arr[idx] = temp;
    }
    return arr;
}
```

# 21
```java
void turnOnOff() {
    isPowerOn = !isPowerOn;
}
void volumeUp() {
    volume += (volume < MAX_VOLUME) ? 1 : 0;
}
void volumeDown() {
    volume -= (volume > MIN_VOLUME) ? 1 : 0;
}

void channelUp() {
    channel += (channel == MAX_CHANNEL) ? 0 : 1;
}
void channelDown() {
    channel += (channel == MIN_CHANNEL) ? 100 : -1;
}
```

# 22
```java
public static boolean isNumber(String str) {
    for(int i=0; i<str.length(); i++) {
        char c = str.charAt(i);
        if(48 > (int)c || (int)c > 57)
            return false;
    }
    return true;
}
```

# 23
```java
public static int max(int[] arr) {
    if (arr == null || arr.length==0)
        return -999999;
    int max = arr[0];
    for (int i : arr) {
        max = i > max ? i : max;
    }
    return max;
}
```

# 24
```java
public static int abs(int value) {
    value *= value < 0 ? -1 : 1;
    return value;
}
```

