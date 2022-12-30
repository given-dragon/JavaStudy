# 1
```java
public static void main(String[] args) {
    Calendar cal = Calendar.getInstance();
    cal.set(2010, Calendar.JANUARY, 1);
    
    for (int i=0; i<12; i++) {
        int day = cal.get(Calendar.DAY_OF_WEEK);

        int secondSunday = (day==1) ? 8 :  8+(8-day);

        cal.set(Calendar.DAY_OF_MONTH, secondSunday);
        Date date = new Date(cal.getTimeInMillis());

        System.out.println(new SimpleDateFormat("yyyy-MM-dd은 F번째 E요일 입니다.").format(date));

        cal.roll(Calendar.MONTH, 1);
        cal.set(Calendar.DAY_OF_MONTH, 1);
    }
}
```

# 2
```java
static int paycheckCount(Calendar from, Calendar to) {

    // ==1==
    if(from==null || to==null)
        return 0;

    // ==2==
    if(from.equals(to) && to.get(Calendar.DAY_OF_MONTH)==21)
        return 1;

    // ==3==
    int fromYear = from.get(Calendar.YEAR);
    int fromMonth = from.get(Calendar.MONTH);
    int toYear = to.get(Calendar.YEAR);
    int toMonth = to.get(Calendar.MONTH);

    int monDiff = (toYear*12+toMonth) - (fromYear*12+fromMonth);

    // ==4==
    if(monDiff<0)
        return 0;

    // ==5==
    int fromDay = from.get(Calendar.DAY_OF_MONTH);
    int toDay = to.get(Calendar.DAY_OF_MONTH);

    if(fromDay <= 21 && toDay >= 21)
        monDiff++;

    // ==6==
    else if (fromDay > 21 && toDay < 21)
        monDiff--;

    return monDiff;
}
```

# 3
```java
public static void main(String[] args) {
    String data = "123,456,789.5";

    DecimalFormat df = new DecimalFormat("#,###.#");
    DecimalFormat df2 = new DecimalFormat("#,####");


    try {
        Number num = df.parse(data);

        double dNum = num.doubleValue();

        System.out.println("data: " + data);
        System.out.println("반올림: " + Math.round(dNum));
        System.out.println("만단위: " + df2.format(dNum));

    } catch (ParseException e) {
        throw new RuntimeException(e);
    }
}
```

# 4
```java
public static void main(String[] args){
    String pattern = "yyyy/MM/dd";
    String pattern2 = "입력하신 날짜는 E요일 입니다.";

    DateFormat df = new SimpleDateFormat(pattern);
    DateFormat df2 = new SimpleDateFormat(pattern2);

    Scanner s = new Scanner(System.in);
    Date inDate;
    do {
        System.out.println("날짜를 " + pattern + "의 형태로 입력해주세요.(입력예:2007/05/11)");
        try {
            System.out.print(">>");
            inDate = df.parse(s.nextLine());
            break;
        } catch(Exception e) {}
    } while(true);

    System.out.println(df2.format(inDate));
}
```

# 5
```java
static int getDayDiff(String yyyymmdd1, String yyyymmdd2) {
    int diff = 0;

    try {
        SimpleDateFormat format = new SimpleDateFormat("yyyyMMdd");

        Date date1 = format.parse(yyyymmdd1);
        Date date2 = format.parse(yyyymmdd2);

        Calendar cal1 = Calendar.getInstance();
        Calendar cal2 = Calendar.getInstance();

        cal1.setTime(date1);
        cal2.setTime(date2);

        diff = (int) ((cal1.getTimeInMillis() - cal2.getTimeInMillis()) / (24*60*60*1000));

    } catch(Exception e) {
        diff = 0;
    }

    return diff;
}
```

# 6
```java
public static void main(String[] args){
    LocalDate birthDay = LocalDate.of(1999,10,30);
    LocalDate now = LocalDate.now();

    long diffDay = birthDay.until(now, ChronoUnit.DAYS);

    System.out.println("birth day="+birthDay);
    System.out.println("today="+now);
    System.out.println(diffDay+" days");
}
```

# 7
```java
import java.time.DayOfWeek;
import java.time.LocalDate;
import java.time.temporal.TemporalAdjusters;
//==============

public static void main(String[] args){
    LocalDate date = LocalDate.of(2016, 12, 1);
    System.out.println(date.with(TemporalAdjusters.dayOfWeekInMonth(4, DayOfWeek.TUESDAY)));
}
```

# 8
```java
public static void main(String[] args){
    ZonedDateTime zdt = ZonedDateTime.now();
    ZoneId nyID = ZoneId.of("America/New_York");
    ZonedDateTime zdtNY = ZonedDateTime.now().withZoneSameInstant(nyID);

    System.out.println(zdt);
    System.out.println(zdtNY);

    long sec1 = zdt.getOffset().getTotalSeconds();
    long sec2 = zdtNY.getOffset().getTotalSeconds();
    long diff = (sec1 - sec2) / (60*60);

    System.out.println("sec1="+sec1);
    System.out.println("sec2="+sec2);
    System.out.printf("diff=%d hrs%n",diff);
}
```

