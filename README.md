Java 8
======
1. Lambda expression   
* 탄생배경   
빅데이터 처리 방법 -> 병렬화 -> 컬렉션 강화 -> 스트림 강화 -> 람다 도입 -> 인터페이스 명세 변경 -> 함수형 인터페이스 도입   
* Lambda ?   
편하게 만들 수 있는 코드 블록!   
익명객체 까지 없이 생성 가능   
<pre>
<code>
public class LambdaExam01 {
  public static void main(String[] args){
  Runnable r = () -> System.out.println("Hello LambdaWorld !");
  
  r.run();
  }
}
</code>
</pre>
추상 메소드를 하나만 갖고 있는 인터페이스 -> 함수형 인터페이스 -> 람다로 변경 가능.   
* 사용방법   
  * 메소드의 인자로 람다식 사용
  * 메소드 반환값으로 람다식 사용
```
public class LambdaExam02 {
  public static void main(String[] args){
  //MyfunctionalInterface mfi = a -> a * a;
    doIt(a -> a * a);
  }
  
  pulbic static void doIt(MyFunctionalInterface mfi){
    int b = mfi.runSomething(5);
    System.out.println(b);
  }
}

@FunctionalInterface
interface MyFunctionalInterface {
  public abstract int runSomething(int count);
}

```
