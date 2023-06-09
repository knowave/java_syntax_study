## 반복문

---

반복문은 프로그램 내에서 똑같은 명령을 일정 횟수만큼 반복해서 수행하도록 제어하는 명령문으로, 프로그램이 처리하는 대부분의 코드는 반복적인 형태가 많으므로, 가장 맣이 사용하는 제어문 중 하나다.

### for 문

```java
public class Loop {
    public static void main(String[] args) {
        int sum = 0;
        
        for (int i = 0; i < 10; i++) {
            sum += (i + 1);    
        }

        System.out.println(sum);    // 55
    }
}
```

위 코드에서 소괄호 안에 맨 왼쪽인 `int i = 0;` 이 부분은 초기화 블럭이다. for 문에 진입할 때, 한 번 실행하는 구문을 이 부분에 써준다. 그래서 `i = 0;`을 `int i` 변수를 선언하고 0을 할당해준다.

`i < 10;`이 부분은 조건문인데 이 반복문을 소괄한 안이 참일 때 수행을 하게된다. 맨 오른쪽에 있는 것은 한 번 실행이 되고, 그 다음 번에 조건에 체크하러 들어오기 전에 그 구문을 입력해주면 된다.

### for-each 문

for-each 문은 배열이나 collection같은 것들을 반복문을 쉽게 짤 수 있는 형태다. 즉, 어떤 것의 나열들이 있는 변수가 있을 때 반복문을 간결하게 짤 수 있는 형태를 말한다.

```java
public class Loop {
    public static void main(String[] args) {
        String[] days = {"Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday", "Sunday"};

        for (String day: days) {
            System.out.println(day);    // Monday Tuesday Wednesday Thursday Friday Saturday Sunday
        }
    }
}
```
위 코드처럼 string 배열 타입의 변수를 선언하고 `for` 뒤에 소괄호를 열어서 소괄호안에 type과 변수이름을 정하고 `:`을 이용해서 `days`를 넣어준 뒤 사용하면 `for`문과는 다르게 더욱 더 간편하게 사용할 수 있다.

### while 문

```java
public class Loop {
    public static void main(String[] args) {
        int i = 0;
        int result = 0;

        while (i < 10) {
            result += (i + 1);
            i++;
        }

        System.out.println(result); // 55
    }
}
```

위 코드보면 for 문과는 다르게 초기화값을 블럭 밖에서 선언을 하고 `while`의 소괄호 안에 밖에서 선언한 `i`를 가져와서 조건문을 써주고, `i`를 증가 시키는 것도 블럭안에서 `i++` 이런식을 처리를 해준다.

만약 블럭 맨 아래에 `i++`을 적어주지 않으면 무한루프에 빠져서 코드가 띁나지 않는다. 왜냐면 i를 증가시켜주지 않고 조건문인 10보다 작으니까 계속해서 실행을 하는것이다.

### do-while 문

```java
public class Loop {
    public static void main(String[] args) {
        int i = 0;
        int sum = 0;

        do {
            sum += (i + 1);
            i++;
        } while (i < 10);

        System.out.println(sum);    // 55
    }
}
```

기존 while 문은 조건을 먼저 확인을 하는데 조건을 확인하지 않고, 수행부터 먼저하는 것이 do-while 문이다.

위에 예시 코드처럼 `do`를 먼저 써주고 `do` 블럭 뒤에 `while (conditional)`을 써주면된다. `do`는 말 그대로 하라는 뜻으로 `do`를 먼저 실행하고, `while`문을 확인해서 조건에 맞으면 계속해서 수행을 하는 것이다. 