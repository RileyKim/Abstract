#추상 클래스
--------

객체를 직접 생성할 수 있는 클래스 : 실체 클래스

클래스들의 공통적인 특성을 추출해서 선언한 클래스 : 추상 클래스

추상 클래스와 실체 클래스는 상속의 관계를 가지고 있다.

추상 클래스가 부모이고 실체 클래스가 자식으로 구현되어 실체 클래스는 추상 클래스의 모든 특성을 물려받고, 추가적인 특성을 가지고 있다. 여기서 특성이란, 필드와 메소드를 말한다.

**추상 클래스는 객체를 직접 생성해서 사용할 수 없다**


```
//추상 클래스
public abstract class Ex{
	// 필드
	// 생성자
	// 메소드
}

```

##추상 클래스의 용도
--------------
첫 번째, 실체 클래스들의 공통된 필드와 메소드의 이름을 통일할 목적

두 번째, 실체 클래스를 작설할 때 시간을 절약


#추상 메소드
----------------

추상 클래스는 추상 메소드를 선언할 수 있다. 추상 메소드는 추상 클래스에서만 선언할 수 있는데 메소드의 선언부만 있고 메소드 실행 내용인 중괄호 {}가 없는 메소드를 말한다.

**추상 클래스를 설계할 때, 하위 클래스가 반드시 실행 내용을 채우도록 강요하고 싶은 메소드가 있을 경우, 해당 메소드를 추상 메소드로 선언한다.**

```
//추상 메소드
public abstract void show(String name);
public abstract int num(int x);
```


```
// 예시
// 추상 클래스 trans.java

package trans;

public abstract class trans {
	
	int[] check = new int[4];
	public abstract int start1(int x); // 시
	public abstract int start2(int x1); // 분
	
	public abstract int stop1(int y); // 시
	public abstract int stop2(int y1); // 분
	public abstract void show(String name); // 교통 수단 이름
}

```



```
// 예시
// 하위 클래스 Bus.java

package trans;

public class Bus extends trans {

	@Override
	public int start1(int x) {
		// TODO Auto-generated method stub
		check[0] = x;
		return check[0];
	}

	@Override
	public int start2(int x1) {
		// TODO Auto-generated method stub
		check[1] = x1;
		return check[1];
	}

	@Override
	public int stop1(int y) {
		// TODO Auto-generated method stub
		check[2] = y;
		return check[2];
	}

	@Override
	public int stop2(int y1) {
		// TODO Auto-generated method stub
		check[3] = y1;
		return check[3];
	}

	@Override
	public void show(String name) {
		// TODO Auto-generated method stub
		System.out.println(name+"의 첫차 시간은" + check[0]+":"+check[1]+"입니다");
		System.out.println(name+"의 막차 시간은" + check[2]+":"+check[3]+"입니다");

	}

}
```



```
//예시
// 하위 클래스 Subway.java

package trans;

public class Subway extends trans {
	


	@Override
	public int start1(int x) {
		// TODO Auto-generated method stub
		check[0] = x;
		return check[0];
	}
	@Override
	public int start2(int x1) {
		// TODO Auto-generated method stub
		check[1] = x1;
		return check[1];
	}

	@Override
	public int stop1(int y) {
		// TODO Auto-generated method stub
		check[2] = y;
		return check[2];
	}
	
	@Override
	public int stop2(int y1) {
		// TODO Auto-generated method stub
		check[3] = y1;
		return check[3];
	}
	@Override
	public void show(String name) {
		// TODO Auto-generated method stub
		
		System.out.println(name+"의 첫차 시간은" + check[0]+":"+check[1]+"입니다");
		System.out.println(name+"의 막차 시간은" + check[2]+":"+check[3]+"입니다");
		
	}

}
```



```
// 예시
// 메인 클래스 MainEnrey.java

package trans;

public class MainEntry {
	public static void main(String[] args) {
		Subway sw = new Subway();
		sw.start1(3);
		sw.start2(45);
		sw.stop1(11);
		sw.stop2(45);
		sw.show("기차");
		
		Bus bus = new Bus();
		sw.start1(4);
		sw.start2(30);
		sw.stop1(12);
		sw.stop2(00);
		sw.show("버스");
	}
}
```
