#### 쓰레드 만들기(extend Thread)

#### 자바에서 Thread를 만드는 방법은 크게 Thread 클래스를 상속받는 방법과 Runnable인터페이스를 구현하는 방법이 있다.

- Thread를 상속 받아서 쓰레드를 생성하는 방법
  - java.lang.Thread클래스를 상속받는다. 그리고 Thread가 가지고 있는 run()메소드를 오버라이딩한다.
  - 10번 반복하면서 str을 찍습니다.

```
    public class MyThread1 extends Thread {
        String str;
        public MyThread1(String str){
            this.str = str;
        }

        public void run(){
            for(int i = 0; i < 10; i ++){
                System.out.print(str);
                try {
                    //컴퓨터가 너무 빠르기 때문에 수행결과를 잘 확인 할 수 없어서 Thread.sleep() 메서드를 이용해서 조금씩 
                    //쉬었다가 출력할 수 있게한다. 
                    Thread.sleep((int)(Math.random() * 1000));
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
            } 
        } 
    }
```

- Thread 클래스를 상속받은 MyThread1을 사용하는 클래스
  - Thread를 상속 받았으므로 MyThread1은 Thread 이다.
  - 쓰레드를 생성하고, Thread 클래스가 가지고 있는 start() 메소드를 호출 한다.

```
    public class ThreadExam1 {
        public static void main(String[] args) {
            // MyThread인스턴스를 2개 만듭니다. 
            MyThread1 t1 = new MyThread1("*");
            MyThread1 t2 = new MyThread1("-");

            t1.start();
            t2.start();
            System.out.print("!!!!!");  
        }   
    }
```
