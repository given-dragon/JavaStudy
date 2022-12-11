# 1
- a. int[] arr[]는 int[][] arr와 동일. -> O
- b. int[] arr2 = {1,2,3,};  //쉼표 있어도 상관 없음. -> O
- d. int[] arr4 = new int[5]{1,2,3,4,5}; //배열의 크기는 {}사이의 개수로 초기화되므로 []안에 크기 지정 안됨. -> X
- e. int arr5[5];    //배열을 선언만 할 경우에는 크기를 정해주지 못함. -> X
- 답 = d, e

# 2
- arr[3]은 { 30, 20 }이므로 크기는 2.

# 3
```java
for (int i : arr) {
    sum += i;
}

// 스트림 사용
sum = Arrays.stream(arr).sum();
```

# 4
```java
int arrLength = 0;
for (int[] row : arr) {
    for (int i : row) {
        total += i;
        arrLength++;
    }
}
average = (float)total/arrLength;

// 스트림 사용
// faltMapToInt를 사용하면 2차원 배열을 단일 원소 스트림으로 리턴받을 수 있다.
total = Arrays.stream(arr).flatMapToInt(Arrays::stream).sum();
average = (float)total/(arr.length*arr[0].length);
```

# 5
```java
// 5-1
tmp = ballArr[i];
ballArr[i] = ballArr[j];
ballArr[j] = tmp;

// 5-2
ball3 = Arrays.copyOf(ballArr, 3);
```

# 6
```java
System.out.println(coinUnit[i]+"원: "+money/coinUnit[i]);
money%=coinUnit[i];
```

# 7
```java
coinNum = money/coinUnit[i];    // (1)
coin[i] = (coin[i] > coinNum) ? coin[i]-coinNum : 0;    // (2)
coinNum = (5-coin[i]);
money -= coinUnit[i]*coinNum;   // (3)
```

# 8
```java
// 8-1
counter[answer[i]-1]++;

// 8-2
System.out.print(counter[i]);
for(int j=0; j<counter[i]; j++){
    System.out.print('*');
}
```

# 9
```java
result[j][(star.length-1)-i] = star[i][j];
```

# 10
```java
if(48 <= ch && ch <= 57)
    result += numCode[ch-48];
else if(97 <= ch && ch <= 122)
    result += abcCode[ch-97];
```

# 11
```java
result[i][j] = score[i][j]; // 3*3배열 복사
result[i][score[0].length] += result[i][j]; // 마지막 열 계산
result[score.length][j] += result[i][j];    // 마지막 행 계산
result[score.length][score[0].length] += result[i][j];  // (4,4)계산
```

# 12
```java
//책이 아직 없어 패스하겠습니다 ㅠ
```

# 13
```java
for(int j=0; j< question.length; j++){
    int randIdx = (int)(Math.random() * question.length);
    char temp = question[j];
    question[j] = question[randIdx];
    question[randIdx] = temp;
}
```