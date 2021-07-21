## 커맨드

요구사항 캡슐화

### 상황

유동적인 요구사항 변화

### BAD solution

1. **확인 후 생성**
   ```java
   class Client {
       private Button[] buttons;
       
       buttons[0] = ...specific code...
       buttons[1] = ...
       
       buttons[0].execute();
    }
   ```
   - 유동적 변화가 어려움

### GOOD solution

1. **커맨드 캡슐화**
   ```java
    class Client {
       Invoker invoker;
       
       invoker.setCommand(new Command(), buttonNum);
       invoker.execute(buttonNum);
    }
    ```
    
    ```java
    class Invoker {
       Command[] commands;
       
       setCommand();
       execute(butttonNum) {
          commands[buttonNum].execute();
       }
    }
    ```
    
    ```java
    interface Command {
       public void execute();
    }
    ```
