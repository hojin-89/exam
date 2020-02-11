Java 8
======
1. Lambda expresion
-------------------
1-1. 탄생배경   
빅데이터 처리 방법 -> 병렬화 -> 컬렉션 강화 -> 스트림 강화 -> 람다 도입 -> 인터페이스 명세 변경 -> 함수형 인터페이스 도입

1-2. Lambda ?   
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

