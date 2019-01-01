---
layout: post
title: '@Configuration과 @Bean'
author: Yoon Hye-Jun
date: 2019-01-01 20:44
---

### @Configuration 에서 2개의 @Bean 으로 구성하였을 경우
```
//BeansConfig.java

package com.example.spring;

import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;

@Configuration
public class BeansConfig {
	@Bean
	public Pizza order() {
		Pizza pizza = new Pizza();
		pizza.setOrder("cheese");
		pizza.setOrder("olive");
		
		return pizza;
	}

	@Bean
	public YumYum bake(Pizza pizza) { // 스프링에 의한 Autowiring by type from bean
		System.out.println("bake a pizza in an oven..");

		YumYum yumYum = new YumYum(pizza.getOrderList());
		
		System.out.println("Completion!");
		return yumYum;
	}
}

```

```

//Test.java

package com.example.spring;

import org.springframework.context.ApplicationContext;
import org.springframework.context.annotation.AnnotationConfigApplicationContext;

public class Test {

	public static void main(String[] args) {
		ApplicationContext context = new AnnotationConfigApplicationContext(BeansConfig.class); // BeansConfig 만 설정하면 된다.
		YumYum yumYum = (YumYum) context.getBean("bake");
		yumYum.getOrderList();
	}

}

```
