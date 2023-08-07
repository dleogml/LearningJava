#### 쓰레드와 상태제어(join)

##### join()메소드는 쓰레드가 멈출때까지 기다리게 한다.

- 일단 0.5초씩 쉬면서 숫자를 출력하는 MyThread5를 작성해 보도록 하겠습니다.

```
    public class MyThread5 extends Thread{
        public void run(){
            for(int i = 0; i < 5; i++){
                System.out.println("MyThread5 : "+ i);
                try {
                    Thread.sleep(500);
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
            }
        } // run
    }
```

- 해당 쓰레드를 실행하고, 해당쓰레드가 종료될때까지 기다린 후, 내용을 출력하는 JoinExam클래스

```
    public class JoinExam { 
        public static void main(String[] args) {
            MyThread5 thread = new MyThread5();
            // Thread 시작 
            thread.start(); 
            System.out.println("Thread가 종료될때까지 기다립니다.");
            try {
                // 해당 쓰레드가 멈출때까지 멈춤
                // MyThread5가 끝날때까지 메인을 잠시 멈춤
                thread.join();
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            System.out.println("Thread가 종료되었습니다."); 
        }   
    }
```

- 실행결과

```
        Thread가 종료될때까지 기다립니다.
        MyThread5 : 0
        MyThread5 : 1
        MyThread5 : 2
        MyThread5 : 3
        MyThread5 : 4
        Thread가 종료되었습니다.
```


