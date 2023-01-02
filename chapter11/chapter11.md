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
        return (int) ((getTotal()/ 3f)*10+0.5)/10f;
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
static int getGroupCount(TreeSet set, int from, int to) {
    Student start = new Student("", 0, 0, from, from, from);
    Student end = new Student("", 0, 0, to, to, to);

    return set.subSet(start, end).size();
}

TreeSet set = new TreeSet(new Comparator() {
    @Override
    public int compare(Object o1, Object o2) {
        if(o1 instanceof Student && o2 instanceof Student) 
            return (int) (((Student) o1).getAverage() - ((Student) o2).getAverage());
        return -1;
    }
});
```

# 7
```java
class BanNoAscending implements Comparator {
    public int compare(Object o1, Object o2) {
        if(!(o1 instanceof Student && o2 instanceof Student))
            return -1;

        Student s1 = (Student) o1;
        Student s2 = (Student) o2;

        return (s1.ban == s2.ban) ? s1.no-s2.no : s1.ban-s2.ban;
    }
}
```

# 8
```java
public int compareTo(Object o) {
    if(!(o instanceof Student))
        return -1;
    
    return ((Student) o).total - this.total;
}

public static void calculateSchoolRank(List list) {
    Collections.sort(list);// 먼저 list를 총점기준 내림차순으로 정렬한다.
    int prevRank = -1; // 이전 전교등수
    int prevTotal = -1; // 이전 총점
    int length = list.size();

    for(int i=0; i<length; i++) {
        Student s = (Student) list.get(i);  // 1

        if(s.total == prevTotal)    // 1.1
            s.schoolRank = prevRank;
        else                        // 1.2
            s.schoolRank = i+1;

        prevRank = s.schoolRank;    // 1.3
        prevTotal = s.total;
    }
}
```

# 9
```java
class ClassTotalComparator implements Comparator {

    public int compare(Object o1, Object o2) {
        if(!(o1 instanceof Student && o2 instanceof Student))
            return -1;

        Student s1 = (Student) o1;
        Student s2 = (Student) o2;
        return s1.ban == s2.ban
                ? s2.total-s1.total
                : s1.ban-s2.ban;
    }
}


public static void calculateClassRank(List list){

        //먼저 반별 총점기준 내림차순으로 정렬한다.
        Collections.sort(list,new ClassTotalComparator());

        int prevBan=-1;
        int prevRank=-1;
        int prevTotal=-1;
        int length=list.size();

        int classRank = 1;
        for(int i=0; i<length; i++) {
            Student s = (Student) list.get(i);  // 1
    
            if(s.ban != prevBan) {  // 1.1
                prevRank = prevTotal = -1;
                classRank = 1;
            }
    
            if(s.total == prevTotal)    // 1.2
                s.classRank = prevRank;
            else                        // 1.3
                s.classRank = classRank++;
    
            prevBan = s.ban;    // 1.4
            prevRank = s.classRank;
            prevTotal = s.total;
        }
}
```

# 10
```java
public static void main(String[] args) {

    Set set = new HashSet();
    int[][] board = new int[5][5];

    for (int i = 0; set.size() < 25; i++) 
        set.add((int) (Math.random() * 30) + 1 + "");
    
    ArrayList list = new ArrayList(set);
    Collections.shuffle(list);

    Iterator it = list.iterator();

    for (int i = 0; i < board.length; i++) {
        for (int j = 0; j < board[i].length; j++) {
            board[i][j] = Integer.parseInt((String) it.next());
            System.out.print((board[i][j] < 10 ? "  " : " ") + board[i][j]);
        }
        System.out.println();
    }
}
```
HashSet은 중복을 허용하지 않고 순서가 바뀌지 않는다.
따라서 숫자를 저장한 후 ArrayList로 옮겨담아 섞어주어야한다.

# 11
```java
class SutdaCard {
    
    ~~~
    public String toString() {
        return num + (isKwang ? "K" : "");
    }
    
    public int hashCode() {
        return toString().hashCode();
    }
}
```
hashCode()의 기본 구현은 클래스명, 메모리주소와 관련된 정수값으로 이루어져 있다. 따라서 객체의 내용이 같아도 다른 해시코드를 갖게 된다.

SutdaCard 클래스에는 toString()을 오버라이딩 하였고, String 클래스의 hashCode()는 문자열 내용을 기반으로 해시코드를 생성한다.

따라서 hashCode()를 오버라이딩 하여 위와 같이 적으면 해당 클래스의 toString()이 반환하는 문자열에 따라서 해시코드를 생성한다.

문자열이 같으면 같은 해시코드를 반환하므로 동일한 내용을 가진 객체가 있다면 중복을 제거할 수 있다.


# 12
```java
void registerJokbo() {
    jokbo.put("KK", 4000); jokbo.put("1010",3100); jokbo.put("99", 3090); jokbo.put("88", 3080); jokbo.put("77", 3070);
    jokbo.put("66", 3060);jokbo.put("55", 3050);jokbo.put("44", 3040);jokbo.put("33", 3030);jokbo.put("22", 3020);
    jokbo.put("11", 3010);jokbo.put("12", 2060);jokbo.put("21", 2060);jokbo.put("14", 2050);jokbo.put("41", 2050);
    jokbo.put("19", 2040);jokbo.put("91", 2040);jokbo.put("110", 2030);jokbo.put("101", 2030);jokbo.put("104", 2020);
    jokbo.put("410", 2020);jokbo.put("46", 2010);jokbo.put("64", 2010);
}

int getPoint(Player p) {

    if (p == null)
        return 0;
    
    SutdaCard c1 = p.c1;
    SutdaCard c2 = p.c2;
    Integer result = 0;
    
    if(c1.isKwang && c2.isKwang)
        result = (Integer) jokbo.get("kk");
    else {
        result = (Integer) jokbo.get("" + c1.num + c2.num);
        if(result == null)
        result =(c1.num+c2.num)%10+1000;
    }
    p.point = result.intValue();
    
    return result.intValue();
}
```

# 13
```java
TreeMap rank = new TreeMap(new Comparator() {
    public int compare(Object o1, Object o2) {
        if(!(o1 instanceof Player && o2 instanceof Player))
            return -1;
        return ((Player) o2).point - ((Player) o1).point;
    }
});
```

# 14
```java
static int displayMenu() {
    
    ~~~
        
    int menu = 0;
    while (true) {
        menu = Integer.parseInt(s.nextLine().trim());   // 1

        if (1<=menu && menu <= 3)
            break;

        System.out.println("메뉴를 잘못 선택하셨습니다. 다시 입력해주세요.");   // 2
        System.out.print("원하는 메뉴를 선택하세요.(1~3):");
    }
    return menu;
}


static void inputRecord() {
    
    ~~~
        
    while (true) {  // 4
        System.out.print(">>");
        try {
            String input = s.nextLine().trim();
        
            if (input.equalsIgnoreCase("q"))    // 2
                return;
        
            Scanner s2 = new Scanner(input).useDelimiter(",");  // 1
            record.add(new Student(s2.next(), s2.nextInt(), s2.nextInt(), s2.nextInt(), s2.nextInt(), s2.nextInt()));
            System.out.println("잘입력되었습니다. 입력을 마치려면 q를 입력하세요.");
        
        } catch (Exception e) { // 3
            System.out.println("입력오류입니다. 이름, 반, 번호, 국어성적, 영어성적, 수학성적'의 순서로 입력하세요.");
        }
    }
}
```
