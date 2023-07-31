#### Byte 단위 입출력 심화

Byte단위 입출력 클래스는 클래스의 이름이 InputStream이나 OutputStream으로 끝납니다.

- 파일로 부터 512byte씩 읽어들여 파일에 512byte씩 저장하는 프로그램을 작성
  - byte[] buffer = new byte[512];
  - 512byte만큼 읽어 들이기 위해 byte배열을 사용

```

    public class ByteIOExam1 {
        public static void main(String[] args){     
            //메소드가 시작된 시간을 구하기 위함
            long startTime = System.currentTimeMillis();        
            FileInputStream fis = null; 
            FileOutputStream fos = null;        
            try {
                fis = new FileInputStream("src/javaIO/exam/ByteExam1.java");
                fos = new FileOutputStream("byte.txt");

                int readCount = -1; 
                byte[] buffer = new byte[512];
                while((readCount = fis.read(buffer))!= -1){
                    fos.write(buffer,0,readCount);
                }
            } catch (Exception e) {
                // TODO Auto-generated catch block
                e.printStackTrace();
            }finally{
                try {
                    fos.close();
                } catch (IOException e) {
                    // TODO Auto-generated catch block
                    e.printStackTrace();
                }
                try {
                    fis.close();
                } catch (IOException e) {
                    // TODO Auto-generated catch block
                    e.printStackTrace();
                }
            }
        //메소드가 끝났을때 시간을 구하기 위함. 
        long endTime = System.currentTimeMillis();
        //메소드를 수행하는데 걸린 시간을 구할 수 있음. 
        System.out.println(endTime-startTime); 
        }
    }

```

- System.currentTimeMillis();  
  - 현재 시간을 롱타입으로 반환한다.
