## 탬플릿 메소드

알고리즘 과정 중 일부 과정 위임

### 상황

동일 과정 중 특정 부분만 다름

### BAD solution

1. **중복 코드 생성**

### GOOD solution

1. **일부 과정 캡슐화**
   ```java
    abstract class Template {
       public final algorithm() {
          do something...
          b();
          do something...
       }
       
       abstract void b();
    }
    ```
    
    ```java
    class Child extends Template {
       @Override
       void b() {
          do child's
       }
    }
    ```
