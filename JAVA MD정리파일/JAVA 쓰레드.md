# Java 쓰레드
## 쓰레드 Thread 란?
: 쓰레드(Thread)란 프로세스(Process) 내에서 실제로 작업을 수행하는 주체를 의미합니다. 모든 프로세스에는 한 개 이상의 쓰레드가 존재하여 작업을 수행합니다. 또한, 두 개 이상의 쓰레드를 가지는 프로세스를 **멀티쓰레드 프로세스(multi-threadedprocess)** 라고 합니다.

## 쓰레드의 생성과 실행
1. Runnable 인터페이스를 구현하는 방법
2. Thread 클래스를 상속받는 방법 <br>
*두 방법 모두 쓰레드를 통해 작업하고 싶은 내용을 run() 메소드에 작성하면 된다*
+ 실행은 start() 로 실행합니다.

## 쓰레드의 우선순위
: 자바에서 각 쓰레드는 우선순위(priority)에 관한 자신만의 필드를 가지고 있습니다. 이러한 우선순위에 따라 특정 쓰레드가 더 많은 시간 동안 작업을 할 수 있도록 설정할 수 있습니다.
+ `static int MAX_PRIORITY` : 쓰레드가 가질 수 있는 최대 우선순위를 명시함.
+ `static int MIN_PRIORITY` : 쓰레드가 가질 수 있는 최소 우선순위를 명시함.
+ `static int NORM_PRIORITY` : 쓰레드가 생성될 때 가지는 기본 우선순위를 명시함.
