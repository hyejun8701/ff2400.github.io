---
layout: post
title: 'Spring Bean'
author: Yoon Hye-Jun
date: 2022-11-21
---

스프링 빈 이란?
=
스프링 빈은 스프링 컨테이너에 의해 관리되는 자바 객체(POJO)를 의미한다.

스프링 컨테이너
=
스프링 컨테이너는 스프링 빈의 생명주기를 관리하며, 생성된 스프링 빈들에게 추가적인 기능을 제공하는 역할을 한다. IoC 와 DI 의 원리가 스프링 컨테이너에 적용된다.
개발자는 new 연산자, 인터페이스 호출, 팩토리 호출 방식으로 객체를 생성하고 소멸하지만, 스프링 컨테이너를 사용하면 해당 역할을 대신해준다.
즉, 제어 흐름을 외부에서 관리하게 된다. 또한, 객체들 간의 의존 관계를 스프링 컨테이너가 런타임 과정에서 알아서 만들어 준다.

스프링 빈 등록 방식
=
Component Scan
-
컴포넌트 스캔은 @Component 를 명시하여 빈을 추가하는 방법이다. 클래스 위에 @Component 를 붙이면 스프링이 알아서 스프링 컨테이너에 빈을 등록한다.

<pre><code>
@Target(ElementType.TYPE)
@Retention(RetentionPolicy.RUNTIME)
@Documented
@Indexed
public @interface Component {
</code></pre>

참고로 @Component 는 위와 같이 ElementType.TYPE 설정이 있으므로 Class, Interface 또는 Enum 에만 붙일 수 있다.

컴포넌트 스캔의 대상
-
@Controller, @Service, @Repository, @Configuration 은 @Component 의 상속을 받고 있으므로 모두 컴포넌트 스캔의 대상이다.

