# java-implements-extends
implements와 extends의 차이

## 상속이란!
> 둘다 상속에 속하고 OOP의 큰 특징중 하나이다!
> 상속은 말 그대로 부모객체로부터 자식객체가 물려받는 것으로 특징 즉 메서드나 변수를 그대로 사용할 수 있다!!
> 상속의 종류로는
  + extends
   > 부모에서 선언/정의를 모두하며 자식은 메서드/ 변수를 그대로 사용할 수 있다.
  + implements(interface 구현)
   > 부모 객체는 선언만 하며 정의(내용)은 자식에서 오버라이딩 (재정의) 해서 사용해야함
  + abstract
   > extends와 interface 혼합. extends하되 몇 개는 추상 메소드로 구현되어 있음
   
## extends(상속)
> 상속의 대표적인 형태이며 부모의 메소드를 그대로 사용할 수 있으며 오버라이딩 할 필요 없이 부모에 구현돼있는 것을 직접 사용 가능하다!

```
  class Vehicle {
  protected int speed = 3;
  
  public int getSpeed(){
    return speed;
  }
  public void setSpeed(int speed){
    this.speed = speed;
  }
}

class Car extends Vehicle{
  public void printspd(){
    System.out.println(speed);
  }
}

public class ExtendsSample {
  public static main (String[] args){
    Car A = new Car();
    System.out.println(A.getSpeed());
    A.printspd();
  }
}
```
> Car은 보는대로 Vehicle을 상속 받았고 메서드를 상속받아 사용했다!
  여기서 Car에 다른 부모를 상속받고 싶다고해도 자바에서는 다중상속을 지원하지 않는다!
  그래서 implements가 등장했다.
  
## implements
```
interface TestInterface{
  public static int num = 8;
  public void fun1();
  public void fun2();
}

class InterfaceExam implements TestInterface{
  @Override
  public void fun1(){
    System.out.println(num);
  }
  
  @Override
  public void fun2() {
    
  }
}

public class InterfaceSample{
  public static void main(String args[]){
    InterfaceExam exam = new InterfaceExam();
    exam.fun1();
  }
}
```
> implements의 가장 큰 특징은 이렇게 부모의 메소드를 반드시 오버라이딩(재정의)해야 한다. 또한 이 implements는 다중상속을 대신해준다.
> 이렇게 사실 다 재정의하면 의미가 있나 싶지만 나름 쓸 만한 이유가 있을거라고 생각이 든다.

## abstract
> 추상 메소드(abstract method)란 자식 클래스에서 반드시 오버라이딩해야만 사용할 수 있는 메소드를 의미한다.
  자바에서 추상 메소드를 선언하여 사용하는 목적은 추상 메소드가 포함된 클래스를 상속받는 자식 클래스가 반드시 추상 메소드를 구현하도록 하기 위함이다.
```
abstract class Animal { abstract void cry(); }

class Cat extends Animal { void cry() { System.out.println("냐옹냐옹!"); } }

class Dog extends Animal { void cry() { System.out.println("멍멍!"); } }

 

public class Polymorphism02 {

    public static void main(String[] args) {

        // Animal a = new Animal(); // 추상 클래스는 인스턴스를 생성할 수 없음.

        Cat c = new Cat();

        Dog d = new Dog();

 

        c.cry();

        d.cry();

    }

}
```
> 자바에서 추상 메소드를 선언하여 사용하는 목적은 추상 메소드가 포함된 클래스를 상속받는 자식 클래스가 반드시 추상 메소드를 구현하도록 하기 위함이다.
  만약 일반 메소드로 구현한다면 사용자에 따라 해당 메소드를 구현할 수도 있고, 안 할 수도 있다. 하지만 추상 메소드가 포함된 추상 클래스를 상속받은 모든 자식 클래스는 추상 메소드를     구현해야만 인스턴스를 생성할 수 있으므로, 반드시 구현하게 된다.
  
