---
title: springboot 如何解决跨域问题
tags:
  - java
---
spring boot 如何解决跨域问题？
在spring config.java 里配置。如下：
```
@Configuration
public class SpringMvcConfig {
    @Bean
    public Filter corsFilter(){
        UrlBasedCorsConfigurationSource source = new UrlBasedCorsConfigurationSource();
        CorsConfiguration config = new CorsConfiguration();
        config.addAllowedOrigin("*");
        config.addAllowedHeader("*");
        config.addAllowedMethod("OPTIONS");
        config.addAllowedMethod("HEAD");
        config.addAllowedMethod("GET");
        config.addAllowedMethod("PUT");
        config.addAllowedMethod("POST");
        config.addAllowedMethod("DELETE");
        config.addAllowedMethod("PATCH");
        source.registerCorsConfiguration("/**", config);
        return new CorsFilter(source);
    }
}

```
@Configration 表示是系统配置。不用在xml文件中配置，项目可以自动执行配置代码
```
config.addAllowedOrigin("*");
```
这句话的意思是设置允许请求的域名。*代表所有的都允许。