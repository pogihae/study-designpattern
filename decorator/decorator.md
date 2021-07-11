## 데코레이터

추가적인 요건을 동적 첨가

### 상황

부가 기능 관리

### BAD solution

1. **부가 기능별 클래스**
   ```java
   class MainWithFunc1, class MainWithFunc2 ....
   ```
   - 너무 많은 클래스
   - 재사용성 낮음

2. **부가 기능 검사**
   ```java
   class Main {
       boolean func1, func2 ...
       
       void addFunc(){
           if(func1) todo...
           if(func2) todo...
           ....
       }
   }
   ```
   - 기능 추가 및 삭제 시 기존 코드 수정 => OCP를 최대한 유지해야함

### GOOD solution

* **부가 기능 서브 클래스**
```java
class Func1 extends Funcs {
    Main m;
    Funcs(Main m){
        this.m = m;
    }
    @Override
    public todo(){
      super.todo();
      other add...
    }
}
```
- 추가 기능으로 덮기 때문에 밑에 세부정보 관리 어려움
```java
Main main = new Main();
main.todo();
main = new Func1(main);
main.todo();
```
