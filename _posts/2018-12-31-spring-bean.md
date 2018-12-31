---
layout: post
title: 'Spring @Configuration @Bean'
author: Yoon Hye-Jun
date: 2018-12-31 15:51
---

```
@Configuration
public class BeansConfig {
  @Bean
  public Say Hello() {
    System.out.println("Hello");
  }
  
  @Bean
  public HelloWorld(Say say) {
    say();
    System.out.println("World!");
  }
}

```
