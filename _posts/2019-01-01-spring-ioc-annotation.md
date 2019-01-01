---
layout: post
title: 'Spring IoC컨테이너와 @Annotation'
author: Yoon Hye-Jun
date: 2019-01-01 20:46
---

#### 이전글에서 IoC컨테이너는 @애너테이션을 붙인 자바 클래스를 스캐닝(탐색)한다고 했었다.

* 그냥 스캐닝 되는 것이 아니고 절차가 있다.
* @애너테이션을 붙인 자바 클래스를 스캐닝하려면 우선 IoC컨테이너를 인스턴스화해야한다.
* 그래야 스프링이 @Configuration, @Bean 을 발견하고 빈 인스턴스를 가져올 수 있다.

1. @Configuration은 이 클래스가 구성 클래스임을 스프링에게 알린다.
2. 스프링은 @Configuration이 달린 클래스를 보면 일단 그 안에서 빈 인스턴스의 정의부, 즉 @Bean을 붙인 메서드를 찾는다.(여기서 메서드는 해당 빈의 인스턴스를 생성해서 반환하는 형태)
```java
@Bean
public Hello hello() {
 return new Hello(); 
}
```
  
3. 구성클래스에 @Bean을 붙이면 그 메서드와 동일한 이름으로 빈이 생성된다.(이름을 명시하려면 @Bean(name="beanName"))
4. 스프링은 기본 구현체인 BeanFactory와 이와 호환되는 구현체 ApplicationContext. 두 가지 IoC컨테이너를 제공한다.
5. 구현체에 자바 구성 클래스를 로드하여 사용한다.
```java
ApplicationContext context = new AnnotationConfigApplicationContext(BeansConfig.class);
```
