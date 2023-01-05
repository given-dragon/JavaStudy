# 1
```java
class Temp {
    public static void main(String[] args) {
        Thread th1 = new Thread(new Thread1());

        th1.start();
    }
}

class Thread1 implements Runnable {
    public void run() {
        for (int i = 0; i < 300; i++) {
            System.out.println('-');
        }
    }
}

OR

class Temp {
    public static void main(String[] args) {
//        익명클래스
//        Thread th1 = new Thread(new Runnable() {
//            @Override
//            public void run() {
//                for (int i = 0; i < 300; i++)
//                    System.out.println('-');
//            }
//        });

//      람다
        Thread th1 = new Thread(() -> {
            for (int i = 0; i < 300; i++)
                System.out.println('-');
        });

        th1.start();
    }
}
```

# 2
- ```.start()```를 실행시켰다면 숫자가 뒤섞여 출력되겠지만 ```.run()```을 실행시켰으므로 단순히 run 메서드를 호출한 것이다. 따라서 0~9까지 순서대로 출력이 된다.

# 3
- b. resume() : suspend()의 호출로 인해 일시정지가 된 쓰레드를 실행대기상태로 바꿔줌.
- f. notify() : wait()으로 일시정지가 된 쓰레드를 실행대기상태로 바꿔줌.

# 4
- d. suspend()에 의하여 일시정지 상태인 쓰레드
- suspend()를 제외한 나머지 메서드들(sleep, join, wait)은 interrupt()가 호출되면 InterruptedException이 발생하여 일시정지 상태에서 벗어나 실행대기 상태가 된다.

# 5
- 1 2 3 4 5 꽝 6 7 8 9 10
- th1이 start된 순간 별도의 호출 스택에서 실행되기 때문에 main에서 5초 뒤 예외가 발생하여 종료되어도 th1은 계속 실행된다.

# 6
- 1 2 3 4 5 꽝
- th1은 데몬스레드이다. 데몬 스레드는 일반 스레드의 작업을 보조하는 역할로, 일반 스레드가 종료되면 함께 종료된다. 따라서 메인 스레드에서 5초 후 예외가 발생하고 종료되면 데몬스레드도 함께 종료된다.

# 7
```java
class Temp {
    static boolean stopped = false;

    public static void main(String[] args) {
        Thread5 th1=new Thread5();
        th1.start();

        try{
            Thread.sleep(6*1000);
        }catch(Exception e){}

        stopped=true; // 쓰레드를 정지시킨다.
        th1.interrupt(); //일시정지 상태에 있는 쓰레드를 깨운다.
        
        System.out.println("stopped");
    }
}

class Thread5 extends Thread {
    public void run() {
        // Exercise13_7.stopped의 값이 false인 동안 반복한다.
        for (int i = 0; !Temp.stopped; i++) {
            System.out.println(i);
            try {
                Thread.sleep(3 * 1000);
            } catch (Exception e) {}
        }
    }
}
```
- 메인스레드에서 stopped 값을 변경해도 th1에서 sleep이 실행되어 일시정지인 상태라면 해당 상태를 벗어날 때까지 기다려야 한다. 따라서 th1.interrupt()로 th1스레드를 깨워주어야 즉시 정지한다.

# 8
```java
class WordGenerator extends Thread {
    public void run() {
        String randData = data[(int) (Math.random() * data.length)];    // 1
        words.add(randData); // 2
        try {
            Thread.sleep(interval);
        } catch (InterruptedException e) {}
    }
}
```

# 9
```java
class Exercise13_9_1 extends Thread {
    public void run() {
        int i = 10;

        while (i != 0 && !isInterrupted()) {
            System.out.println(i--);

            try {
                Thread.sleep(1000); // 1초 지연
            } catch (InterruptedException e) {
                interrupt();
            }
        }
        System.out.println("카운트가 종료되었습니다.");
    }
}
```
- sleep()에 의해 스레드가 일시정지 상태일 경우 interrupt()을 호출하게 되면 InterruptedException가 발생한다. 그리고 스레드의 isInterrupted값을 false로 초기화 된다.
- 따라서 catch 블록에 interrupt()를 한번 더 넣어주어 isInterrupted값을 true로 바꾸어주어야 한다.
- 