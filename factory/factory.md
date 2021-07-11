## 팩토리

생산자 분리

### 상황

다양한 제품군 존재

### BAD solution

1. **조건 분기**
   ```java
   class Client {
       Product product;
       
       if(a) product = new A();
       if(b) product = new B();
       
       product.execute();
    }
   ```
   - 코드의 복잡성
   - OCP 안 지켜짐

### GOOD solution

1. **팩토리 메소드**
   ```java
    abstract class Client {
      Product product;
    
      void use(){
          product = createProcuct();
          product.execute();
      }
    
      abstract void createProduct();
    }
    ```
    - 서브 클래스 생성으로 관리
2. **추상 팩토리**
    ```java
    abstract class Factory {
        abstract void createIngedient1();
        abstract void createIngedient2();
        abstract void createIngedient3();
    }
    ```
    - 하나의 객체로 관리
    - 
