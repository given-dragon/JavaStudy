# 1
```java
for(int i=0; i<CARD_NUM; i++) {
    if(i==0 || i==2 || i==7)
        cards[i] = new Temp.SutdaCard(i+1, true);
    else
        cards[i] = new Temp.SutdaCard(i%10+1, false);
}
```

# 2
```java
public void shuffle() {
    for (int i = 0; i < CARD_NUM; i ++) {
        int idx = (int) (Math.random() * 20);
        SutdaCard temp = cards[i];
        cards[i] = cards[idx];
        cards[idx] = temp;
    }
}

public SutdaCard pick(int index) {
        return cards[index];
}

public SutdaCard pick() {
        int idx = (int) (Math.random()*20);
        return cards[idx];
    }
```

# 3
```java
부모 클래스의 메서드를 자식 클래스에서 재정의 하는 것.
부모 클래스의 메서드는 자식 클래스에서 사용하지 못할 수 있어 재정의 필요. 
```

# 4
- c. 접근 제어자는 조상의 메서드보다 좁은 범위로만 변경할 수 있다. 
- d. 조상의 메서드보다 더 많은 수의 예외를 선언할 수 있다.

# 5
- 부모 클래스에 기본 생성자를 추가해주면 된다.
- 자식의 기본생성자는 컴파일 시 super()가 자동으로 생성된다. 이는 부모 클래스의 기본생성자를 실행시키는 코드이므로 에러가 발생한다.


# 6
- 자손 클래스에는 조상 클래스의 인스턴스 변수도 함께 생성된다. 따라서 조상 클래스의 인스턴스 변수도 초기화를 해주어야 한다.

# 7
- Child() -> Child(int x) -> Parent() -> Parent(int x)

# 8
- a. public - protected - (default) - private

# 9
- c. 메서드 - 오버로딩을 할 수 없다. --> 오버라이딩을 할수없음

# 10
```java
class MyTv2 {
    private boolean isPowerOn; 
    private int channel; 
    private int volume;
    final int MAX_VOLUME = 100; 
    final int MIN_VOLUME = 0; 
    final int MAX_CHANNEL = 100; 
    final int MIN_CHANNEL = 1;
    
    public boolean getIsPowerOn() {
        return isPowerOn;
    }
    public void setIsPowerOn(boolean isPowerOn) {
        this.isPowerOn = isPowerOn;
    }
    public int getChannel() {
        return channel;
    }
    public void setChannel(int channel) {
        this.channel = channel;
    }
    public int getVolume() {
        return volume;
    }    
    public void setVolume(int volume) {
        this.volume = volume;
    }
}
```

# 11
```java
class MyTv2 {
    private boolean isPowerOn;
    private int channel;
    private int volume;
    private int prevChannel;
    final int MAX_VOLUME = 100;
    final int MIN_VOLUME = 0;
    final int MAX_CHANNEL = 100;
    final int MIN_CHANNEL = 1;

    public void gotoPrevChannel() {
        int temp = channel;
        channel = prevChannel;
        prevChannel = temp;
    }

    public boolean getIsPowerOn() {
        return isPowerOn;
    }
    public void setIsPowerOn(boolean isPowerOn) {
        this.isPowerOn = isPowerOn;
    }
    public int getChannel() {
        return channel;
    }
    public void setChannel(int channel) {
        prevChannel = this.channel;
        this.channel = channel;
    }
    public int getVolume() {
        return volume;
    }
    public void setVolume(int volume) {
        this.volume = volume;
    }
}
```

# 12
- c. 지역변수에도 접근 제어자를 사용할 수 있다. -> private과 public만 사용 가능


# 13
- Math 클래스는 모든 메서드가 static이다. 즉 인스턴스가 없다. 따라서 생성자를 호출할 필요가 없기 때문이다.

# 14
```java
final int num;
final boolean isKwang;
```

# 15
- e. t = (Tank)u; -> u는 Tank의 부모이다. 부모는 자식으로 형변환이 불가능하다.

# 16
- d. fe instanceof Ambulance

# 17
```java
class Unit {
    int x, y; //현재 위치 
    void move(int x, int y) { /* 지정된 위치로 이동 */ }
    void stop() { /*현재 위치에 정지 */ }
}

class Marine extends Unit { // 현재 위치
    void stimPack() { /* 스팀팩을 사용한다.*/}
}

class Tank extends Unit { //탱크
    void changeMode()  { /* 공격모드를 변환한다. */} 
}

class Dropship extends Unit { //수송선
    void load()  { /* 선택된 대상을 태운다.*/ }
    void unload()  { /* 선택된 대상을 내린다.*/ } 
}
```

# 18
```java
public static void action(Robot robot) {
    if(robot instanceof DanceRobot)
        ((DanceRobot) robot).dance();
    else if (robot instanceof SingRobot)
        ((SingRobot) robot).sing();
    else if (robot instanceof DrawRobot)
        ((DrawRobot) robot).draw();
}
```

# 19
```java
void buy(Product p) {
    if(p.price > money) {
        System.out.println("잔액이 부족하여 " + p.toString() + "을(를) 살수 없습니다.");
        return;
    }

    money -= p.price;
    add(p);
}

void add(Product p) {
    if(i>=cart.length) {
        Product[] newCart = new Product[cart.length * 2];
        System.arraycopy(cart, 0, newCart, 0, cart.length);
        cart = newCart;
    }
    cart[i++] = p;
}

void summary() {
    int totalPrice = 0;
    StringBuilder cartList = new StringBuilder();
    for(Product p : cart){
        cartList.append(p.toString()).append(", ");
        totalPrice += p.price;
    }
    
    System.out.println("구입한 물건: " + cartList);
    System.out.println("사용한 금액: " + totalPrice);
    System.out.println("남은 금액: " + money);
}
```

# 20
- p.x = 100
- Child Method
- p.x = 200
- Child Method

# 21
- Movable의 구현체
- null

# 22
```java
class Circle extends Shape{
    double r;
    
    public Circle(double r){
        this.r = r;
    }

    @Override
    double calcArea() {
        return r*r*Math.PI;
    }
}

class Rectangle extends Shape {
    double width;
    double height;

    public Rectangle(double width, double height) {
        this.width = width;
        this.height = height;
    }

    @Override
    double calcArea() {
        return width*height;
    }

    boolean isSquare() {
        return width==height;
    }
}
```

# 23
```java
public static double sumArea(Shape[] arr) {
    double sum = 0;
    for(Shape s : arr) {
        sum += s.calcArea();
    }
    return sum;
}
```

# 24
- e. 패키지간의 연결을 도와준다.

# 25
```java
Outer outer = new Outer();
Outer.Inner inner = outer.new Inner();
System.out.println(inner.iv);
```

# 26
```java
Outer.Inner inner = new Outer.Inner();
System.out.println(inner.iv);
```

# 27
```java
(1) System.out.println(value);
(2) System.out.println(this.value);
(3) System.out.println(Outer.this.value);
(4) Outer outer = new Outer();
    Outer.Inner inner = outer.new Inner();
    inner.method1();
```

# 28
```java
public static void main(String[] args) {
    Frame f = new Frame();
    f.addWindowListener(new WindowAdapter() {
        public void windowClosing(WindowEvent e) {
            e.getWindow().setVisible(false);
            e.getWindow().dispose();
            System.exit(0);
        }
    });
}
```

# 29
- 책이 아직 없어서 정확한 답을 잘 모르겠네요 ㅠㅠ
- 일단 패스 하겠습니다!