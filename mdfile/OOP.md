## OOP

---

### Class

어떤 속성을 갖는지와 어떤 모양을 갖는지는 미리 틀을 만들어서 정해져있는 것이다. 예를 들어 붕아빵 틀로 표현하자면 밀가루 반죽을 붓고 팥을 붓고 불을 그을리면 붕어빵이 나오듯이 이 틀을 통해서 만들어진 붕어빵을 **Instance**라고 생각하면 된다.

Instance는 만들어지면서 각 다르지만 모습은 동일하게 가지고 있다. 한 번 생성되고 나면 그 자체의 상태를 가지고 그 자체로 변화를 하게된다.

```java
class Phone {
    String model;
    String color;
    int price;
}

public class OOP {
    public static void main(String[] args) {
        Phone galaxy = new Phone();
        galaxy.model = "Galaxy10";
        galaxy.color = "Black";
        galaxy.price = 100;

        Phone iphone =new Phone();
        iphone.model = "iPhoneX";
        iphone.color = "Black";
        iphone.price = 200;


        System.out.println("철수는 이번에 " + galaxy.model + galaxy.color + " + 색상을 " + galaxy.price + "만원에 샀다.");
        System.out.println("영희는 이번에 " + iphone.model + iphone.color + " + 색상을 " + iphone.price + "만원에 샀다.");
    }
}
```

class 내부에 있는 method를 사용하기 위해서는 인스턴스화가 필요하다.
```java
class Calculation {
    int add(int x, int y) {
        return x + y;
    }

    int subtract(int x, int y) {
        return x - y;
    }
}

public class OOP {
    public static void main(String[] args) {
        // write your code here
        Calculation calculation = new Calculation(); // 인스턴스화를 시켜준다.
        int addResult = calculation.add(1, 2); // 인스턴스화를 시킨 변수를 이용하여 method를 호출한다.
        int subtractResult = calculation.subtract(2, 1); // 인스턴스화를 시킨 변수를 이용하여 method를 호출한다.

        System.out.println(addResult); // 3
        System.out.println(subtractResult); // 1
    }
}
```

#### 생성자 (constructor)

생성자는 **Instance**가 생성될 때 즉, `new`라는 키워드를 통해서 class의 instance를 생성했을 때 그때 불리는 초기화 method이다. (new를 통해서 불러와짐.)

생성자의 형식은 class의 이름이 있으면 class의 이름이랑 똑같은 이름으로 지어줘야 한다. (생성자의 규칙) 그리고 생성자는 리턴값이 없다. `new` 키워드를 사용하면 그 개체 결과가 return이 되지 특별히 다른 값이 return이 되지 않듯이 return값이 없다.

생성자를 만들어주지 않으면 Java compiler가 아무것도 없는 빈 생성자 하나를 자동으로 만들어줘서 `new class()`를 해서 괄호 안에 아무 값을 넣지않고 Instance를 생성할 수 있는 것이다.

```java
class Phone {
    String model;
    String color;
    int price;

    public Phone (String model, String color, int price) { // 생성자 이름은 class 이름과 같아야한다.
        this.model = model; // this. 뒤에 있는 model은 위에서 정의한 model이다.
        this.color = color;
        this.price = price;
    }
}

public class OOP {
    public static void main(String[] args) {
        Phone galaxy = new Phone();

        Phone iphone =new Phone();

        System.out.println("철수는 이번에 " + galaxy.model + galaxy.color + " + 색상을 " + galaxy.price + "만원에 샀다.");
        System.out.println("영희는 이번에 " + iphone.model + iphone.color + " + 색상을 " + iphone.price + "만원에 샀다.");
    }
}
```

### 상속

**상속**은 <u>**기존의 클래스를 재사용하는 방식 중의 하나**</u>로 한 번 작성한 코드가 재사용이 필요하다면 변경사항만 코드로 작성하여 상대적으로 적은 양의 코드를 작성할 수 있다.

클래스를 재사용하여 코딩을 한다면 코드와 클래스가 많아질수록 관리가 용이하다는 장점이 존재하며 상속을 통해서 클래스간의 계층구조를 만들게 된다.

상속의 특징으로는 아래와 같다.
1. 부모 클래스에서 정의된 필드와 메서드를 물려 받는다.
2. 새로운 필드와 메서드를 추가할 수 있다.
3. 부모 클래스로부터 물려받은 메서드를 수정할 수 있다.

상속을 보여주는 **UML Class Diagram**이 존재하는데, 자동차라는 클래스가 있으면 하위 계층으로 SUV와 SEDAN이 존재한다.

![](https://velog.velcdn.com/images/kwaktaemin_/post/8989533f-4873-40da-a18f-9d0b0888082c/image.png)

위 그림과 같이 Car Class는 부모 클래스가 되고, SUV와 SEDAN Class는 자식 Class가 된다.

```java
class Animal {
    String name;

    public void cry() {
        System.out.println(name + " is crying.");
    }
}

class Dog extends Animal {
    public Dog(String name) {
        this.name = name;
    }

    public void swim() {
        System.out.println(name + " is swimming.");
    }
}

public class OOP {
    public static void main(String[] args) {
        // write your code here
        Dog dog = new Dog("강아지");
        dog.cry();
        dog.swim();

        Animal dog2 = new Dog("왈왈");
        dog2.cry();
    }
}
```

**상속은 여러 Class를 상속받을 수 없으며, 하나의 Class만 상속을 받을 수 있다.**

### overloading

**overloading**은 한 Class 내에서 동일한 이름의 method를 여러개 갖는 것을 의미하는데, <u>하지만 이름이 같다고 해서 무조건 overloading은 아니다.</u>

어떤 조건이냐면 method 이름이 첫 번째로 동일해야하고, 매개 변수의 개수나 type이 달라야한다. 또한 return type이 다른 경우는 overloading으로 치지 않는다.

```java
public class OOP {
    public static void main(String[] args) {
        // write your code here
    }

    int add(int x, int y, int z) {
        return x + y + z;
    }

    long add(int a, int b, long c) {
        return a + b + c;
    }
}
```
### overriding

overriding은 부모의 class로부터 상속받은 method 즉, 부모 class에 있는 method를 똑같이 자식 class에 정의를 하는 것을 의미한다. 이런 작업을 통해서 덮어 버린다고 이해하면 좋을 것 같다. (부모에 있던 원래 함수의 내용은 없는 셈)

```java
class Animal {
    String name;
    String color;

    public Animal(String name) {
        this.name = name;
    }

    public void cry() {
        System.out.println(name + " is crying.");
    }
}

class Dog extends Animal {
    public Dog(String name) {
        super(name);
    }

    @Override
    public void cry() {
        System.out.println(name + " is barking.");
    }
}

public class OOP {
    public static void main(String[] args) {
        // write your code here
        Animal dog = new Dog("강아지");
        dog.cry();
    }
}
```

### 접근제어자

**접근제어자**는 멤버 변수와 함수 혹은 클래스에 사용되고, 외부에서의 접근을 제한하는 역할을 한다.

- private: 같은 클래스 내에서만 접근이 가능하다.
- default(nothing): 같은 패키지 내에서만 접근이 가능하다.
- protected: 같은 패키지 내에서, 그리고 다른 패키지의 자식 클래스에서 접근이 가능하다.
- public: 접근 제한이 없다.

```java
package pkg; // package 경로 이름

public class ModifierTest {
    private void messageInside() { // 같은 클래스 안에 있는 것이 접근 가능
        System.out.println("This is private Modifier");
    }

    public void messageOutside() {
        System.out.println("This is public Modifier");
        messageInside(); // 같은 클래스 내부에서 접근이 가능하므로 호출
    }

    protected void messageProtected() {
        System.out.println("This is protected Modifier");
    }
}

```

```java
import pkg.ModifierTest;

class Child extends ModifierTest {
    void callParentProtected() {
        System.out.println("Call my parent's protected method");
        super.messageProtected(); // super는 상속 받은 부모 클래스를 가리키는 키워드
    }
}

public class OOP {
    public static void main(String[] args) {
        ModifierTest modifierTest = new ModifierTest();
        modifierTest.messageOutside(); // This is public Modifier / This is private Modifier

        Child child = new Child();
        child.callParentProtected(); // Call my parent's protected method / This is protected Modifier
    }
}
```

OOP 클래스에서 modifierTest 클래스를 받고 `messageOutside()` 메서드를 실행시켰더니 `This is public Modifier / This is private Modifier`가 출력되었다.

아까 `pkg` 패키지에서 `ModifierTest` 구현체를 보면 public 메서드 인 `messageOutside()`에서 `private messageInside()` 메서드를 호출해줬기 때문에 `This is private Modifier`가 출력이 될 수 있다.

`modifierTest.messageInside()`를 하면 `private`이라 당연히 불러올 수 없고, `modifierTest.messageProtected()`도 불러올 수 없다.

그 이유는 `modifierTest.messageProtected()`의 제어자는 `protected`이기 때문이다. 위에 설명했듯이 같은 패키지내에서 혹은 다른 패키지의 자식 클래스 안에서 사용할 수 가 있다.

그래서 `Child` 클래스를 인스턴스화 해주고 `child.callParentProtected()`를 하면 protected 타입인 `messageProtected()`를 호출할 수 있다.

또한 `Child` 클래스의 `void CallParentProtected()` 메서드는 앞에 아무것도 안 붙어있기 때무에 패키지 privete이다. 그럼 어떻게 호출이 되냐면 

최상위 아무것도 없는 Java 밑에 있는 것이기 때문에 호출이 되고, 하지만 다른 패키지에서 아무 제한자를 정하지 않은채 넘긴다면 다른 패키지에서 불러올 수 없다.

### 추상클래스

**추상클래스**란 추상메서드를 선언할 수 있는 클래스를 의미한다. 또한 <u>**추상클래스는 클래스와는 다르게 상속받는 클래스 없이 그 자체로 인스턴스를 생성할 수 없다.**</u>

추상메서드는 설계만 되어있고, **수행되는 코드에 대해서는 작성이 안된 메서드다.** 이처럼, 미완성으로 남겨두는 이유는 <u>**상속받는 클래스마다 반드시 동작이 달라지는 경우에 상속받는 클래스는 개발자가 반드시 작성하도록하기 위함이다.**</u>

```java
abstract class Bird {
    private int x,y,z;
    
    void fly(int x, int y, int z) {
        printLocation();
        System.out.println("이동합니다.");
        
        this.x = x;
        this.y = y;
        
        if(flyable(z)) {
            this.z = z;
        } else {
            System.out.println("그 높이로는 날 수 없습니다.");
        }
        
        printLocation();
    }
    
    abstract boolean flyable(int z);
    
    public void printLocation() {
        System.out.println("현재 위치 {" + x + ", " + ", " + y + ", " + z + "}");
    }
}

class Pigeon extends Bird {
    @Override
    boolean flyable(int z) {
        return z < 10000;
    }
}

class Peacock extends Bird {
    @Override
    boolean flyable(int z) {
        return false;
    }
}

public class OOP {
    public static void main(String[] args) {
        Bird pigeon = new Pigeon();
        Bird peacock = new Peacock();

        System.out.println("pigeon");
        pigeon.fly(1, 1, 3);

        System.out.println("peacock");
        peacock.fly(1, 1, 3);

        System.out.println("pigeon");
        pigeon.fly(1, 1, 30000);
    }
}
```

추상클래스를 만들 떄, `abstract`를 class 앞에 적어줘서 추상클래스를 만들어주고 그 클래스안에서 해당 로직을 짜주는데, 본인은 날지 못하는 새에 대해서 추상메서드를 만들어줬다.

추상메서드도 추상클래스와 똑같이 앞에 `abstract`를 붙여서 추상 메서드를 만들 수 있다. 하지만 추상메서드를 만들 때 주의할 점은 중괄호를 뒤에 붙여주면 에러가 발생하는데, 추상메서드의 body는 `abstract methods`가 가질 수 없기 때문이다.

추상클래스는 인스턴스화를 할 수 없기 때문에 자식 클래스를 이용하여 인스턴스를 하는데, 자식클래스인 `Bird`를 인스턴스를 기존에 했던 것들 처럼 하면 에러가 발생한다. 그 이유는 추상 클래스를 인스턴스화 할 수 없기 때문이다.

추상클래스를 불러오기 위해서는 다른 구현체에서 상속받아서 추상메서드를 구현해줘야 한다. 본인은 `Pigeon`이라는 클래스를 만들어서 `@override` 어노테이션을 이용해서 추상메서드의 이름과 동일하게 구현을 해준다. 

### 인터페이스

**인터페이스**는 객체의 특정 행동의 특징을 정의하는 간단한 문법이다. 인터페이스는 함수의 특징인 접근제어자, 리턴타입, 메서드 이름만 정의한다.

함수의 로직은 없고, 인터페이스를 구현하는 클래스는 인터페이스에 존재하는 함수의 로직을 반드시 구현해야 한다.

```java
interface Flyable {
    void fly(int x, int y, int z);
}

class Pigeon implements Flyable { // extends로 클래스를 상속하는 키워드와 다르게 인터페이스는 implements로 가져온다.
    private int x, y, z;
    
    @Override
    public void fly(int x, int y, int z) {
        System.out.println("구국구");
    }
}

public class OOP {
    public static void main(String[] args) {}
}
```

위에서 설명했듯이 인터페이스는 메서드를 구현하지 않고 **body**없이 남겨두고 인터페이스를 사용하는 클래스에서 **body**를 구현해줘야한다.

추상클래스와 비슷하게 인터페이스를 사용하는 클래스 내부에 override 어노테이션을 사용해서 로직을 구현한다. 인터페이스에서는 필드도 정의하지 않았기 때문에 인터페이스를 사용하는 클래스에서 필드정의도 해준다.

그리고 상속과는 다르게 여러개의 인터페이스를 구현할 수 있다. 단, 메서드 내용을 클래스 내부에서 구현만 해준다면 가능하다.