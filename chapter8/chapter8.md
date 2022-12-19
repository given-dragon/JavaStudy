# 1
- 정의: 프로그램 실행 시 발생할 수 있는 예외의 발생에 대비한 코드를 작성하는 것
- 목적: 프로그램의 비정상 종료를 막고, 정상적인 실행상태를 유지하는 것

# 2
- d. method2가 method1을 호출하였고 그 위치는 Exception18.java파일의 8번째 줄이다. => main->method1->method2 순서대로 호출되었다.

# 3
- d. void add(int a, int b) throws Exception{}
- e. void add(int a, int b) throws NumberException{}

Exception과 NumberException은 InvalidNumberException과 NotNumberException보다 상위 메서드이다.
따라서 더 많은 예외를 던진다.
오버라이딩을 할 때 조상 메서드보다 더 많은 예외를 처리할 수 없다.

# 4
- c. try {method();} catch(Exception e) {} catch(NumberException e) {}

Exception은 가장 상위의 예외이므로 모든 예외를 처리할 수 있다.
catch문이 여러개일 경우 순서대로 검사하게된다.
Exception은 모든 예외를 처리할 수 있기 때문에 가장 마지막에 위치해야 한다.

# 5
- method(true): 1 3 5
- method(false): 1 2 5 6

# 6
- 3 5

# 7
- method(true): 1

exit(0)이면 프로그램이 종료된다.

# 8
```java
public static void main(String[] args) {
    // 1~100 사이의 임의의 값을 얻어서 answer에 저장한다.
    int answer = (int) (Math.random() * 100) + 1;
    int input = 0; // 사용자입력을 저장할 공간
    int count = 0; // 시도횟수를 세기 위한 변수

    do {
        count++;
        System.out.print("1과 100사이의 값을 입력하세요 :");
        
        try {
            input = new Scanner(System.in).nextInt();
        } catch (InputMismatchException e) {
            count--;
            System.out.println("유효하지 않은 값입니다. 다시 값을 입력해주세요.");
            continue;
        }

        if (answer > input) {
            System.out.println("더 큰 수를 입력하세요 .");
        } else if (answer < input) {
            System.out.println("더 작은 수를 입력하세요 .");
        } else {
            System.out.println("맞췄습니다 .");
            System.out.println("시도횟수는 " + count + "번입니다 .");
            break; // do-while문을 벗어난다
        }
    } while (true);
}
```

# 9
```java
class UnsupportedFuctionException extends RuntimeException {
    private final int ERR_CODE;

    public UnsupportedFuctionException(String msg, int ERR_CODE) {
        super(msg);
        this.ERR_CODE = ERR_CODE;
    }

    public UnsupportedFuctionException(String msg) {
        this(msg, 100);
    }

    public int getErrorCode() {
        return ERR_CODE;
    }

    @Override
    public String getMessage() {
        return "["+getErrorCode()+"]"+super.getMessage();
    }
}
```

# 10
- 2 4 7

