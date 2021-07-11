## 옵저버

일대다 정보 갱신

### 상황

정보를 주는 객체 하나와 받는 객체 여려개

### BAD solution

1. **주는 객체에서 받는 객체 직접 호출**
   ```java
   class Subject {
       void update(Data data1, Data data2 ...){
           observer1.update(data1, data2 ...);
           observer2.update(data1, data2 ...);
           ...
       }
    }
   ```
   - 받는 객체들의 추가 및 삭제가 어려움
   - 동적 변경 어려움 = 런타임 시 변경이 어렵다

### GOOD solution

* **느슨한 결합**
```java
class MyData extends Subject {
    List<Observer> subscribes;
    Data data1, data2, data3;
    
    void notify(){
        for(Observer o : subscribes){
            //pull, observer call get 
            o.update(this);
            //push
            o.update(Data data1, Data data2, Data data3);
        }
    }
}
```
- Observer이라는 다형성을 구현할 수 있게 선언
- 각각의 객체를 몰라도 됨, 느슨한 결합
- 리스트를 활용해 추가, 삭제가 용이

```java
class Subscriber extends Observer {
    //pull, only get 1 and 2 not 3
    void update(Subject s){
        this.data1 = s.getData1();
        this.data2 = s.getData2();
    }
    //push
    void update(Data data1, Data data2, Data data3){
        this.data1 = data1;
        this.data2 = data2;
        //data3 is not used
    }
}
```
- Subject에서 받아온다는 것만 알고 있고, 그것을 구현함
