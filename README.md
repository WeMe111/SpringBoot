# 스프링부트
***프로젝트 기간: 2022.04.20 ~ 2022.05.11***

## 목차

## 개념정리

### SpringBoot 란?
Spring framework 기반 프로젝트를 복잡한 설정없이 쉽꼬 빠르게 만들어주는 라이브러리.  
개발자가 일일히 모든 설정을 할 필요없이 자주 사용되는 기본 설정을 알아서 해준다.  
스프링 부트는 실행만 하면 스프링기반의 사용화가 가능한 애플리케이션을 쉽게 만들기 위해 단독 실행 가능하도록 해주는 스프링 프로젝트이다.  
[참고](https://cheershennah.tistory.com/194)  

### Thymeleaf 와 jsp 비교 분석
**Thymeleaf**  
Thymeleaf는 HTML, XML, JavaScript, CSS 및 일반 텍스트를 처리 할 수 있는 웹 및 독립형 환경에서 사용할 수 있는 Java 템플릿 엔진입니다.     Thymeleaf는 html파일을 가져와서 파싱해서 분석후 정해진 위치에 데이터를 치환해서 웹 페이지를 생성합니다.  

**장단점**  
Thymeleaf 템플릿 엔진의 장점은 페이지를 생성하는데 필요한 정보를 태그의 속성으로 넣고, remove 속성을 이용해서 실제 생성될 페이지에서는 제거될 태그를 넣을 수 있어서 페이지의 프로토타입을 제공할 수 있다는 것입니다.  
Thymeleaf로 작성된 페이지를 웹 브라우저로 열어보면 실제 보여질 내용과 동일하게 보여집니다.  

**jsp**  
JSP는 서블릿으로 변환되어 실행이 되어집니다. JSP 내에서 자바 코드를 사용할 수도 있습니다(사용하지 못하도록 설정할 수 있습니다). Thymeleaf는 자바코드를 사용할 수 없고, jsp에서 처럼 커스텀 태그와 같은 기능도 없습니다.  

**장단점**  
JSP는 사실 서블릿이다보니 뭐든지 할 수 있다는게 장점이자 단점이 되겠습니다. MVC 구조가 주로 사용되면서 JSP는 뷰만 담당하고, JSP에 비즈니스 로직을 넣으면 디버깅 및 유지보수가 힘들어진다고 하여 요즘은 JSP에서는 자바 코드를 사용하지 못하게 하는게 일반적입니다.  
[참고](https://suzyalrahala.tistory.com/39)  

### Maven과 Gradle의 차이
**Maven이란?**  
프로젝트를 진행하면서 사용하는 수많은 라이브러리들을 관리해주는 도구입니다.  
여기서 메이븐의 특징적인 점은 그 라이브러리들과 연관된 라이브러리들까지 거미줄처럼 모두 연동이 되서 관리가 된다는 점입니다.  
즉, 메이븐은 네트워크를 통해 연관된 라이브러리까지 같이 업데이트를 해주기 때문에  사용이 편리합니다.  

**Gradle이란?**  
Gradle이란 기본적으로 빌드 배포 도구(Build Tool)이다. 안드로이드 앱을 만들때 필요한 공식 빌드시스템입니다.  
빌드툴인 Ant Builder와 그루비 스크립트를 기반으로 구축되어 기존 Ant의 역할과 배포 스크립트의 기능을 모두 사용가능하다.  
기본 메이븐의 경우 XML로 라이브러리를 정의하고 활용하도록 되어 있으나, Gradle의 경우 별도의 빌드스크립트를 통하여 사용할 어플리케이션 버전, 라이브러리등의 항목을 설정 할 수 있다.  
장점으로는 스크립트 언어로 구성되어 있기때문에, XML과 달리 변수선언, if, else, for등의 로직이 구현가능하여 간결하게 구성 가능하다.  

**Gradle이 Maven보다 좋은점**  
- Build라는 동적인 요소를 XML로 정의하기에는 어려운 부분이 많다.  
- 설정 내용이 길어지고 가독성 떨어짐  
- 의존관계가 복잡한 프로젝트 설정하기에는 부적절  
- 상속구조를 이용한 멀티 모듈 구현  
- 특정 설정을 소수의 모듈에서 공유하기 위해서는 부모 프로젝트를 생성하여 상속하게 해야함 (상속의 단점 생김)  
- Gradle은 그루비를 사용하기 때문에, 동적인 빌드는 Groovy 스크립트로 플러그인을 호출하거나 직접 코드를 짜면 된다.  
- Configuration Injection 방식을 사용해서 공통 모듈을 상속해서 사용하는 단점을 커버했다.  
- 설정 주입시 프로젝트의 조건을 체크할 수 있어서 프로젝트별로 주입되는 설정을 다르게 할 수 있다.  
- Gradle은 메이븐보다 최대 100배 빠르다.  

### 타임리프 기본 문법
변수 : ${...} - ${student.id}  
선택자 : *{...} - *{id}  
메시지 : #{...} - #{id}  
링크URL : @{...} - @{https://www.naver.com}  
부분적 표현 : ~{...} -  
조건 연산자 : and, or, not, !  
${student.age} > 20 and ${student.age} < 10 처럼 각각 분리하여서 사용하거나  
${student.age > 20 or student.age < 10} 처럼 한 번에 묶어서 사용하는 것도 가능  
텍스트 결합 : ${student.id}+${student.name}  
문장 결합 : |학생 아이디 : ${student.id}, 학생 이름 : ${student.name} | - | 로 전체 문장을 묶어줌  
if-then : if ? then - ${student.age < 20} ? '청소년'  
if-then-else : if ? then : else - ${student.age < 20} ? '청소년' : '성인'  
default : value ?: defaultValue  
[참고](https://sujinhope.github.io/2021/03/25/Thymeleaf-2.-Thymeleaf-%EA%B8%B0%EB%B3%B8-%EB%AC%B8%EB%B2%95-+-%EC%82%AC%EC%9A%A9-%EC%98%88%EC%A0%9C.html#title2)  

### Repository vs Service 의 역할의 차이점
repository 패키지는 DB에 접근하는 모든 코드가 모여있다고 생각하시면 되고  
service 패키지는 DB에 접근하는 코드는 repository에 위임하고, 비즈니스 로직과 관련된 모든 코드가 모여있습니다.  
이렇게 구분해두면 비즈니스 로직과 관련된 부분에 문제가 발생했을 때는 service 패키지를 확인하고, DB 접근과 관련된 문제가 발생하면 repository 부분을 확인하면 됩니다.

## 환결설정

## 도메인 분석 설계
### Member Entity 
```
@Entity
@Getter
@Setter
public class Member {
	
	@Id @GeneratedValue
	@Column(name = "member_id")
	private Long id;
	
	private String name;
	
	@Embedded
	private Address address;
	
	@OneToMany(mappedBy = "member")
	private List<Order> order = new ArrayList<>();
}
```  
***@Id, @GenerratedValue***: 기본키를 자동으로 생성할 때에는 @Id와 @GenerratedValue 어노테이션이 함께 사용되어야 한다.
[참고](https://velog.io/@gudnr1451/GeneratedValue-%EC%A0%95%EB%A6%AC)  
***@Column***: 객체 필드를 테이블의 컬럼에 매핑시켜주는 애노테이션이다.
[참고](https://ttl-blog.tistory.com/114)  
***@OneToMany***: 단반향으로 하게되면 문제점이 많아 mappedBY를 설정해줘서 양방향으로 만들어준다.
[참고](https://dublin-java.tistory.com/51)  
***@Embedded***: 새로운 값 타입을 직접 정의해서 사용할 수 있다.
[참고](https://velog.io/@conatuseus/JPA-%EC%9E%84%EB%B2%A0%EB%94%94%EB%93%9C-%ED%83%80%EC%9E%85embedded-type-8ak3ygq8wo)  


![image](https://user-images.githubusercontent.com/94879395/164642968-41a52dc7-a1bc-46ba-815a-a3918e7b6e2d.png)  

### Addrres
```
@Embeddable
@Getter
public class Address {
	
	private String city;
	private String street;
	private String zipcode;
	
	protected Address() {
	 }
	
	public Address(String city, String street, String zipcode) {
		 this.city = city;
		 this.street = street;
		 this.zipcode = zipcode;
	 }
}
```  
***@Embeddable***: 값 타입을 정의하는 곳에 표시  

### Order
```
@Entity
@Table(name = "orders")
@Getter @Setter
public class Order {

	@Id @GeneratedValue
	@Column(name = "order_id")
	private Long id;
	
	@ManyToOne(fetch = FetchType.LAZY)
	@JoinColumn(name = "member_id")
	private Member member;
	
	@OneToMany(mappedBy = "order", cascade = CascadeType.ALL)
	private List<OrderItem> orderItem = new ArrayList<>();
	
	@OneToOne(cascade = CascadeType.ALL, fetch = FetchType.LAZY)
	@JoinColumn(name = "delivery_id")
	private Delivery delivery;
	
	private LocalDateTime orderDate;  //주문시간
	
	@Enumerated(EnumType.STRING)
	private OrderStatus status;  //주문상태 [oder, cancel]
  
}
```  
***@Table***: 엔티티와 매핑할 테이블을 지정, 생략 시 매핑한 엔티티 이므로 테이블 이름(Order)으로 사용
[참고](https://data-make.tistory.com/610)  
***@ManyToOne***: 외래키가 있는 곳에 참조를 걸고 연관관계 매핑을 한다.  
[참조](https://jyami.tistory.com/21)  
***@OneToOne***:  [참고](https://ict-nroo.tistory.com/126)  
***@JoinColumn***:  조인컬럼은 외래키를 매핑할 때 사용한다. name 속성에는 매핑할 외래키 이름을 지정한다.
[참고](https://yellowh.tistory.com/121)  
***@Enumerated***:  @Enumerated(EnumType.ORDINAL)
[참고](https://lng1982.tistory.com/280)  
                    -> enum 순서 값을 저장  
                    @Enumerated(EnumType.STRING)  
                    -> enum 이름을 저장  
```
public enum OrderStatus {
	ORDER, CANCEL  //데이터의 값을 정의해서 쓸 수 있다.
}

```
***LocalDateTime***: 날짜와 시간 정보 모두가 필요할 때 사용.  

![image](https://user-images.githubusercontent.com/94879395/165016978-86de5604-0a96-470e-a3f6-3e76223633c2.png)  
## 회원 도메인 
### MemberRepository
```
@Repository
public class MemberRepository {
	
	@PersistenceContext
	private EntityManager em;
	
	public void save(Member member) {
		em.persist(member);
	}

	public Member findOne(Long id) {
		return em.find(Member.class, id);
	}
	
	public List<Member> findAll(){
		return em.createQuery("select m from Member m", Member.class)
				.getResultList();
	}
	
	public List<Member> findByName(String name) {
		 return em.createQuery("select m from Member m where m.name = :name",
		Member.class)
		 .setParameter("name", name)
		 .getResultList();
		 }
}
```  
***@Repository***: Entity에 의해 생성된 DB에 접근하는 메서드(ex) findAll()) 들을 사용하기 위한 인터페이스이다. 위에서 엔티티를 선언함으로써 데이터베이스 구조를 만들었다면, 여기에 어떤 값을 넣거나, 넣어진 값을 조회하는 등의 CRUD(Create, Read, Update, Delete)를 해야 쓸모가 있는데, 이것을 어떻게 할 것인지 정의해주는 계층이라고 생각하면 된다.
[참고](https://whitepro.tistory.com/265)  
***@PersistenceContext***: EntityManagerFactor객체는 고객의 요청이 올 때마다 즉, 각 쓰레드마다 EntityManager 객체를 생성하고 해당 객체는 내부적으로 DB Connection Pool을 활용하여 DB에 연결을 합니다.
[참고](https://jaimemin.tistory.com/1898)  
***persist***: ...

### MemberServise
```
@Service
@Transactional(readOnly = true)
@RequiredArgsConstructor
public class MemberService {

	private final MemberRepository memberRepository;

	/**
	 * 회원가입
	 */
	@Transactional // 변경
	public Long join(Member member) {
		validateDuplicateMember(member); // 중복 회원 검증
		memberRepository.save(member);
		return member.getId();
	}

	private void validateDuplicateMember(Member member) {
		List<Member> findMembers = memberRepository.findByName(member.getName());
		if (!findMembers.isEmpty()) {
			throw new IllegalStateException("이미 존재하는 회원입니다.");
		}
	}

	/**
	 * 전체 회원 조회
	 */
	public List<Member> findMembers() {
		return memberRepository.findAll();
	}

	public Member findOne(Long memberId) {
		return memberRepository.findOne(memberId);
	}
}

```  
***@Transactional***: 데이터베이스의 상태를 변경하는 작업 또는 한번에 수행되어야 하는 연산들을 의미한다.
[참고](https://velog.io/@kdhyo/JavaTransactional-Annotation-%EC%95%8C%EA%B3%A0-%EC%93%B0%EC%9E%90-26her30h)  
***@RequiredArgsConstructor***: final 필드에 대해 생성자를 만들어주는 lombok의 annotation  
## 상품 도메인 개발
### ItemRepository
```
@Repository
@RequiredArgsConstructor
public class ItemRepository {
	private final EntityManager entityManager;
	
	public void save(Item item) {
		if(item.getId() == null) {
			entityManager.persist(item);
		}else {
			entityManager.merge(item);
		}
	}
	
	public Item findOne(Long id) {
		return entityManager.find(Item.class, id);
	}
	
	public List<Item> findAll(){
		return entityManager.createQuery("select i from Item i", Item.class)
				.getResultList();
	}
}
```
*** ***
### ItemService
```
@Service
@Transactional(readOnly = true)
@RequiredArgsConstructor
public class ItemService {
	private final ItemRepository itemRepository;

	@Transactional
	public void saveItem(Item item) {
		itemRepository.save(item);
	}

	public List<Item> findItems() {
		return itemRepository.findAll();
	}

	public Item findOne(Long itemId) {
		return itemRepository.findOne(itemId);
	}
}
```

## 기타

## 오류

## 후기
