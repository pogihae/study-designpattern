## 스트래티지

알고리즘군 분리 캡슐화

### 상황

기능 추가

### BAD solution

1. **부모 클래스에 구현 후 상속**
   ```java
   class Parent {
       void newFunc() {
           todo....
       }
    }
   ```
   - 서브 클래스 별 기능차이 구현 어려움 => 오류 발생가능
   - 동적 변경 어려움 = 런타임 시 변경이 어렵다

2. **기능의 인터페이스화**
   ```java
   class Child extends Parent implements NewFuncalbe {
       @Override
       void newFunc(){
           todo....
       }
   }
   ```
   - 코드 재사용성이 떨어짐 => 각 서브 클래스 별 구현 해야함
   - 동적 변경 어려움

### GOOD solution

* **기능의 캡슐화**
```java
class Parent {
    NewFunc nf
    
    void func(){
        nf.execute();
    }
}
```
```java
class Child extends Parent {
    Child(NewFunc nf) {
        this.nf = nf;
    }
}
```
