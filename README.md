Java 8
======
## 1. Lambda expression   
* 탄생배경   
빅데이터 처리 방법 -> 병렬화 -> 컬렉션 강화 -> 스트림 강화 -> 람다 도입 -> 인터페이스 명세 변경 -> 함수형 인터페이스 도입   
* Lambda ?   
편하게 만들 수 있는 코드 블록!   
익명객체 까지 없이 생성 가능
```
public class LambdaExam01 {
  public static void main(String[] args){
  Runnable r = () -> System.out.println("Hello LambdaWorld !");
  
  r.run();
  }
}
```
추상 메소드를 하나만 갖고 있는 인터페이스 -> 함수형 인터페이스 -> 람다로 변경 가능.   
* 사용방법   
  * 메소드의 매개변수로 람다식 사용
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
* 함수형 인터페이스 제공   
java.util.function 패키지로 다양한 함수형 인터페이스를 제공   
<https://docs.oracle.com/javase/8/docs/api/java/util/function/package-summary.html>   
   
      
         
 
## 2. Stream API   
* Stream API ?
많은 양의 배열 컬렉션 데이터를 정형화된 처리 패턴의 방법 제공   
* 생성 가능한 데이터 소스들
  * 컬렉션.stresm(), 배열.stream(),    
  가변 매개변수 Stream.of(), 지정 범위의 연속 변수 (Long)IntStream.range(),    
  특정 타입 난수 Random().int(4),    
  람다 Stream.iterate()/generate(),   
  파일 Files.lines(Path path),    
  빈 스트림 Stream.empty()
* 특징
  * 한 번만 사용 가능.
  * 원본 데이터 변경 x
  * 병렬 처리 지원
* 동작 흐름
  * 스트림 생성 -> 중개 연산(스트림 변환) -> 최종 연산(스트림 사용)
```
public class StreamExam {
  public static void main(String[] args){
    ArrayList<Integer> list = new ArrayList<Integer>();
    list.add(4);
    list.add(2);
    list.add(3);
    list.add(1);
		
    Stream<Integer> stream = list.stream();
    stream.forEach(System.out::println);		
  }
}
```
* 중개 연산
  * 스트림 필터링 : filter(), distinct()
  * 스트림 변환 : map(), flatMap()
  ```
  Stream<String> stream = Stream.of("HTML", "CSS", "JAVA", "JAVASCRIPT");
  
  stream.map(s -> s.length()).forEach(System.out::println);
  ```
  * 스트림 제한 : limit(), skip()
  * 스트림 정렬 : sorted()
  * 스트림 연산 결과 확인 : peek()
* 최종 연산
  * 요소의 출력 : forEach()
  * 요소의 소모 : reduce()
  * 요소의 검색 : findFirst(), findAny()
  * 요소의 검사 : anyMatch(), allMatch(), noneMatch()
  * 요소의 통계 : count(), min(), max()
  * 요소의 연산 : sum(), average()
  * 요소의 수집 : collect()
  ```
  public static void main(String[] args){
    Stream<String> stream = Stream.of("넷", "둘", "하나", "셋");
    
    List<String> list = stream.collect(Collectors.toList());
    Iterator<String> iter = list.iterator();
    while (iter.hasNext()) {
			System.out.print(iter.next() + " ");
		}
	}
  ```
* API   
<https://docs.oracle.com/javase/8/docs/api/java/util/stream/package-summary.html>
