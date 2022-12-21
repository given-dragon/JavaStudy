# 1
```java
public boolean equals(Object obj) {
    if(!(obj instanceof SutdaCard))
        return false;
    
    SutdaCard s = (SutdaCard) obj;
    return (this.num==s.num) && (this.isKwang&&s.isKwang);
}
```

# 2
```java
public boolean equals(Object obj) {
    if(!(obj instanceof Point3D))
        return false;

    Point3D p = (Point3D) obj;
    return (this.x==p.x) &&(this.y==p.y) &&(this.z==p.z);
}
```

# 3
```java
int idx = fullPath.lastIndexOf('\\');   // 문자열 우측부터 탐색
path = fullPath.substring(0, idx);  // 0~idx까지 출력
fileName = fullPath.substring(idx+1);   //idx+1부터 출력
```

# 4
```java
static void printGraph(int[] dataArr, char ch){
    for (int data : dataArr) {
        for (int i = 0; i < data; i++) {
            System.out.print(ch);
        }
        System.out.println(data);
    }
}
```

# 5
```java
public static int count(String src, String target){
    int count = 0;
    int pos = 0;

    while((pos = src.indexOf(target, pos)) != -1){
        count++;
        pos+=target.length();
    }
    
    return count;
}
```

# 6
```java
public static String fillZero(String src, int length){
    if(src==null || src.length()==length)
        return src;
    else if(length <= 0)
        return "";
    else if(src.length() > length)
        return src.substring(0, length);
    else{
        char[] dst = new char[length];
        for (int i = 0; i < length; i++)
            dst[i] = '0';
        System.arraycopy(src.toCharArray(), 0, dst, length-src.length(), src.length());
        return new String(dst);
    }
}
```

# 7
```java
public static boolean contains(String src, String target){
    return src.indexOf(target)!=-1;
}
```

# 8
```java
public static double round(double d, int n){
    double pow = Math.pow(10, n);
    return Math.round(d*pow) / pow;
}
```

# 9
```java
public static String delChar(String src, String delCh){
    StringBuilder sb = new StringBuilder();

    for(int i=0; i<src.length(); i++) {
        char c = src.charAt(i);
        if(delCh.indexOf(c) == -1)
        sb.append(c);
    }
    return sb.toString();
}
```

# 10
```java
public static String format(String str, int length, int alignment){
    int diff = length - str.length();
    if(diff < 0)
        return str.substring(0, length);

    char[] source = str.toCharArray();
    char[] result = new char[length];

    for (int i = 0; i < result.length; i++)
        result[i] = ' ';

    switch (alignment) {
        case 0:
        default:
            System.arraycopy(source, 0, result, 0, source.length);
            break;
        case 1:
            System.arraycopy(source, 0, result, diff/2, source.length);
            break;
        case 2:
            System.arraycopy(source, 0, result, diff, source.length);
            break;
    }

    return new String(result);
}
```

# 11
```java
public static void main(String[] args) {
    int start = 0;
    int end = 0;

    try{
        if(args.length != 2)
            throw new Exception("시작 단과 끝 단, 두 개의 정수를 입력해주세요.");
        start = Integer.parseInt(args[0]);
        end = Integer.parseInt(args[1]);

        if(start < 2 || 9 < start || end < 2 || 9 < end)
            throw new Exception("단의 범위는 2와 9사이의 값이어야 합니다.");

        if(start > end) {
            int temp = start;
            start = end;
            end = temp;
        }

        for (int i = start; i <= end; i++) {
            for (int j = 1; j <= 9; j++) {
                System.out.println(i+"*"+j+"="+i*j);
            }
            System.out.println();
        }

    } catch (Exception e) {
        System.out.println(e.getMessage());
    }
}
```

# 12
```java

```

# 13
```java

```

# 14
```java

```

