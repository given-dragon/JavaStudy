# 1
```java
public static void main(String[] args) {
    int lineNum = Integer.parseInt(args[0]);
    String fileName = args[1];

    File file = new File(fileName);

    if (!file.exists() || file.isDirectory())
        return;

    try {
        BufferedReader br = new BufferedReader(new FileReader(file));

        String line;
        for (int i=1; i<=lineNum; i++) {
            if ((line = br.readLine()) == null)
                return;
            System.out.println(i + ":" + line);
        }

    } catch (Exception e) {
        System.out.println(e);
    }
}
```

# 2
```java
public static void main(String[] args) {
    if (args.length != 1) {
        System.out.println("USAGE: java HexaViewer FILENAME");
        System.exit(0);
    }

    String inputFile = args[0];

    try{
        FileInputStream input = new FileInputStream(inputFile);

        int data = 0;
        int i=0;

        while ((data = input.read()) != -1) {
            System.out.printf("%02x ", data);
            if (++i % 16 == 0)
                System.out.println();
        }

        input.close();
    } catch (Exception e) {
        System.out.println(e);
    }
}
```

# 3
```java
public static void countFiles(File dir) {
    File[] files = dir.listFiles();
    if (files == null)
        return;

    for (File file : files) {
        if (file.isDirectory()) {
            totalDirs++;
            countFiles(file);
        }
        totalFiles++;
        totalSize += file.length();
    }

}
```

# 4
```java
public static void main(String[] args) {
    if (args.length < 2) {
        System.out.println("USAGE: java FileMergeTest MERGE_FILENAME FILENAME1 FILENAME2 ...");
        System.exit(0);
    }

    try {
        ArrayList<FileInputStream> arr = new ArrayList<>();

        for (int i = 1; i < args.length; i++) {
            File file = new File(args[i]);

            if(file.exists())
                arr.add(new FileInputStream(args[i]));
            else {
                System.out.println(args[i] + " - 존재하지 않는 파일입니다.");
                System.exit(0);
            }
        }

        SequenceInputStream input = new SequenceInputStream(Collections.enumeration(arr));
        FileOutputStream output = new FileOutputStream(args[0]);

        int data = 0;
        while ((data = input.read()) != -1) 
            output.write(data);
        
    } catch (Exception e) {
        e.printStackTrace();
    }
}
```

# 5
```java
public void write(int c) throws IOException{

    if (c == '<')
        inTag = true;
    else if (c == '>') {
        inTag = false;
        tmp = new StringWriter();
        return;
    }

    (inTag ? tmp : out).write(c);
}
```

# 6
```java
public static void cd() {
    if (argArr.length == 1) {
        System.out.println(curDir);
        return;
    } else if (argArr.length > 2) {
        System.out.println("USAGE:cddirectory");
        return;
    }

    String subDir = argArr[1];

    if ("..".equals(subDir)) {
        File newDir = curDir.getParentFile();

        if (newDir == null) {
            System.out.println("유효하지 않은 디렉토리입니다.");
        } else {
            curDir = newDir;
        }
    } else if (".".equals(subDir)) {
        System.out.println(curDir);
    } else {
        File newDir = new File(curDir, subDir);
        if (newDir.exists() && newDir.isDirectory()) {
            curDir = newDir;
        } else {
            System.out.println("유효하지 않은 디렉토리입니다.");
        }
    }
}
```

# 7
```java
public static void saveAs(String FileName) {
    FileWriter fw = null;
    BufferedWriter bw = null;
    
    try {
        fw = new FileWriter(fileName);
        bw = new BufferedWriter(fw);
        bw.write(ta.getText());
    } catch (IOException e) {
        e.printStackTrace();
    } finally {
        try {
            if(bw != null)
                bw.close();
        } catch(IOException e) {}
    }
}
```

# 8
```java
void display(int pos) { // pos위치에 있는 라인의 내용을 보여준다.
    String pData = wordList.get(pos).toString();
    StringBuffer stringBuffer = new StringBuffer(pData.length());
    StringTokenizer stringTokenizer = new StringTokenizer(pData, "|");

    while (stringTokenizer.hasMoreTokens()) 
        stringBuffer.append(stringBuffer);
    
    ta.setText(stringBuffer.toString());
}

void loadFile(String fileName) {
    try {
        BufferedReader bufferedReader = new BufferedReader(new FileReader(fileName));
        String line = "";

        while((line = bufferedReader.readLine()) != null)
            wordList.add(line);
        
    } catch (Exception e) {
        System.out.println("데이터 파일을 읽을 수 없습니다.");
        System.exit(0);
    }
}
```

# 9
```java
void fileOpen(String fileName) {
    FileReader fr = null;
    BufferedReader br = null;
    StringWriter sw = null;
    
    try {
        fr = new FileReader(fileName);
        br = new BufferedReader(fr);
        sw = new StringWriter();
        
        String line = "";
        
        while ((line=br.readLine()) != null) {
            sw.write(line);
            sw.write('\n');
        }
        
        content.setText(sw.toString());
    } catch (IOException e) {
        e.printStackTrace();
    } finally {
        try {
            if (br != null)
                br.close();
        } catch (IOException e) {}
    }
}

void saveAs(String fileName) {
    FileWriter fw = null;
    BufferedWriter bw = null;

    try {
        fw = new FileWriter(fileName);
        bw = new BufferedWriter(fw);
        bw.write(content.getText());

    } catch (IOException e) {
        e.printStackTrace();
    } finally {
        try {
            if(bw != null)
                bw.close();
        } catch (IOException e) {}
    }
}
```
