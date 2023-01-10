# 1
```java
public static void main(String args[]) {
    byte[] ip = {(byte) 192, (byte) 168, (byte) 10, (byte) 100};
    byte[] subnet = {(byte) 255, (byte) 255, (byte) 255, (byte) 0};

    byte[] nwAddress = new byte[4];
    byte[] hostAddress = new byte[4];

    System.out.print("네트워크 주소:");
    for (int i = 0; i < ip.length; i++) {
        nwAddress[i] = (byte) (ip[i] & subnet[i]);
        System.out.print((nwAddress[i]>=0 ? nwAddress[i] : nwAddress[i]+256)+".");
    }

    System.out.println();

    System.out.print("호스트 주소:");
    for (int i = 0; i < ip.length; i++) {
        hostAddress[i] = (byte) (ip[i] & ~subnet[i]);
        System.out.print((hostAddress[i]>=0 ? hostAddress[i] : hostAddress[i]+256)+".");
    }

    System.out.println();
}
```

# 2
- c. UDP보다 전송속도가 빠르다. -> 느림

# 3
```java
void displaySource() {
    URL url = null;
    BufferedReader input = null;
    String address = tf.getText().trim();
    String line = "";
    
    ta.setText("");
    
    try {
        if (!address.startsWith("http://"))
            address = "http://" + address;

        url = new URL(address);
        input = new BufferedReader(new InputStreamReader(url.openStream(), "UTF-8"));

        while((line=input.readLine()) != null){
            ta.append(line);
            ta.append("\n");
        }

        input.close();

    } catch (Exception e) {
        ta.setText("유효하지 않은 URL입니다.");
    }

}
```

# 4
```java
void startServer() {
    ServerSocket serverSocket = null;
    Socket socket = null;

    try {
        serverSocket = new ServerSocket(7777);
        ta.setText("서버가 준비되었습니다.");
        
        socket = serverSocket.accept();
        ta.append("\r\n" +"상대방과 연결되었습니다.");

        while (in != null) {
            String msg = in.readUTF();
            ta.append("\r\n" + msg);
        }
    } catch (Exception e) {
        e.printStackTrace();
    }
}
```
