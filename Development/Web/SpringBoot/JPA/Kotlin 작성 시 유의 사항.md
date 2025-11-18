---
title: Kotlin 작성 시 유의 사항
date: 2022-11-06
type:  blog
author: harris baek
email: baekjh09@naver.com
---
tags: #spring , #backend , #db, #jpa , #kotlin


## 1. Kotlin에서의 Entity 정의

```ad-error
title: Data class 금지
data 클래스의 경우 기본 생성자에 정의한 Property들만 Copy, hashCode, toString에 활용 된다. 그러므로 클래스를 잘못 저으이하면 hashCode나 equals등이 잘못 동작할 가능성이 크다.

또한 Setter가 기본적으로 public 되어 있으므로 캡슐화가 되지않는다.
```

### 1.1 기존 Kotlin Entity 하지 말아야 할점
Kotlin은 불변(immutable)을 지향한다. 변수(mutable)은 부작용이 많기 때문이다. 그러나 웹상의 코드들을 보면 너무 Mutable을 낭비하는 코드들을 볼 수 있다.

```kotlin
@Entity 
class Person( 
	@ID 
	var id: Long, 
	@Column 
	var name: String, 
	@Column 
	var age: Int, 
)
```

위 코드의 **문제점은 캡슐화가 전혀 되어있지않다**. (외부에서 누구나 Enitty에 set 및 데이터를 알수 있다) 심지어 Entity에서 바꾸지 말아야 할 식별자 까지 바꿀 수 있도록 저으이 한것은 정말 치명적이다.



### 1.2 All Open 및 No arg 추가
기본적으로 JPA는 기본 생성자를 이용하여 Entity를 구성하므로, 모든 Entity에 기본 생성자를 구현 해줘야 한다. 아래 플러그인 추가시에 컴파일시 모든 클래스의 기본 생성자를 만든다.

```kotlin
  
plugins { 
	...
//코틀린 버전은 맞춰서 변경
   kotlin("plugin.jpa") version "1.7.0"  
   kotlin("plugin.spring") version "1.7.0"
}
```


JPA는 프록시 기반으로 Lazy 로딩을 하는데, Proxy는 상속 기반이므로 final이 붙은 클래스를 open 해줘야 한다. 그래서 JPA를 사용하는 경우 다음과 같은 설정을 추가한다.
```kotlin
allOpen {
    annotation("javax.persistence.Entity")
    annotation("javax.persistence.MappedSuperclass")
    annotation("javax.persistence.Embeddable")
}
```


### 1.3 Protected set, Back Properties 통한 캡슐화
var로 설정하게 되면 외부에서 쉽게 값을 변경 가능하게 되므로 최대한 캡슐화를 위해서 protected로 setter를 설정한다.

```kotlin
  
@Entity  
class Person(  
    name: String  
) {  
    @Id  
    @GeneratedValue    
    var id: Long? = null  

	//setter를 최대한 막아준다.
    @Column(nullable = false)  
    var name: String = name  
		protected set

	//백프로퍼티를 통해서 mutableList의 값 추가 권한를 private하게 변경
    @OneToMany(mappedBy = "person", cascade = [CascadeType.ALL], orphanRemoval = true, fetch = FetchType.LAZY)  
	private val _positions: MutableList<Position> = mutableListOf()  
	val positions: List<Position> get() = _positions
```


