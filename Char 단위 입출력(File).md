#### Char 단위 입출력(File)

char단위 입출력 클래스는 클래스 이름이 Reader나 Writer로 끝이 납니다.

- 파일에서 한 줄씩 입력 받아서 파일에 출력
  - 파일에서 읽기위해서 FileReader 클래스 이용
  - 한 줄 읽어 들이기 위해서 BufferedReader 클래스 이용
    - BufferedReader 클래스가 가지고 있는 readLine() 메소드가 한줄씩 읽게 해준다.
    - readLine()메소드는 읽어낼 때 더 이상 읽어 들일 내용이 없을 때 null을 리턴한다.
  - 파일에 쓰게하기 위해서 FileWriter 클래스 이용
  - 편리하게 출력하기 위해서 PrintWriter 클래스 이용

```

    import java.io.BufferedReader;
    import java.io.FileReader;
    import java.io.FileWriter;
    import java.io.IOException;
    import java.io.PrintWriter; 
    public class CharIOExam02 {
        public static void main(String[] args) {
            BufferedReader br = null; 
            PrintWriter pw = null;
            try{        
                br = new BufferedReader(new FileReader("src/javaIO/exam/CharIOExam02.java"));
                pw = new PrintWriter(new FileWriter("test.txt"));
                String line = null;
                while((line = br.readLine())!= null){
                    pw.println(line);
                }
            }catch(Exception e){
                e.printStackTrace();
            }finally {
                pw.close();
                try {
                    br.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
        }
    }
```
