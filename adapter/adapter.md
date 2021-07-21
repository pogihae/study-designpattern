## 어댑터

인터페이스 변환

### 상황

새로운 인터페이스 클라이언트에 구 인터페이스 사용해야함

### BAD solution

1. **새로 생성**
  
   - 기존 클라이언트들 수정이 필요함

### GOOD solution

1. **어댑터 인터페이스 구현**
   ```java
    interface Adapter extends newInterface {
       
    }
    ```
    
    ```java
    class Adaptee implements Adapter {
       
       Adaptee(oldInterface){}
       
       @Override
       void newfunc() {
          oldInterface.oldFunc();
          ...modify
       }
    }
    ```
