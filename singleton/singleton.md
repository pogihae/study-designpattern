## 싱글톤

객체 생성 제한

### 상황

하나의 인스터스만 사용되어야 함

### BAD solution

1. **확인 후 생성**
   ```java
   class SingleTon {
       private static SingleTon obj = null;
       
       private SingleTon(){};
       
       public static SingleTon getObj(){
           if(obj == null) return obj = new SingleTon();
           else return obj;
       }
    }
   ```
   - 멀티스레드 환경에서 두개의 인스턴스가 생성가능함

### GOOD solution

1. **게터 동기화**
   ```java
    class SingleTon {
       private static SingleTon obj = null;
       
       private SingleTon(){};
       
       public static synchronized SingleTon getObj(){
           if(obj == null) return obj = new SingleTon();
           else return obj;
       }
    }
    ```
    - 속도가 떨어짐 => 처음 한번만 상호배제가 필요하기 때문에 과도한 배제임
2. **미리 생성**
    ```java
    class SingleTon {
       private static SingleTon obj = new Object();
       
       private SingleTon(){};
       
       public static SingleTon getObj(){
           return obj;
       }
    }
    ```
    - 확인 필요없음
    - 로딩 후 사용가능
3. **DCL**
    ```java
   class SingleTon {
       private volatile static SingleTon obj = null;
       
       private SingleTon(){};
       
       public static SingleTon getObj(){
           if(obj == null){
              synchronized{
                  if(obj == null) obj = new SingleTon();
              }
           }
           return obj;
       }
    }
   ```
