title: Spring Boot启动时自动打开浏览器
author: felix1982
tags: []
categories:
  - spring boot
date: 2018-12-27 23:15:00
---
  > 这是一个开发小技巧,可以省去每次启动Spring Boot后自己打开浏览器，输入URL的麻烦。
  
~~~
@SpringBootApplication
public class SpringBootDemoApplication {

    public static void main(String[] args) {
        SpringApplication.run(SpringBootDemoApplication.class, args);
        String url = "http://localhost:8063";
        if(Desktop.isDesktopSupported()){
            Desktop desktop = Desktop.getDesktop();
            try {
                desktop.browse(new URI(url));
            } catch (IOException e) {
                e.printStackTrace();
            } catch (URISyntaxException e) {
                e.printStackTrace();
            }
        }else{
            Runtime runtime = Runtime.getRuntime();
            try {
                runtime.exec("rundll32 url.dll,FileProtocolHandler " + url);
            } catch (IOException e) {
                // TODO Auto-generated catch block
                e.printStackTrace();
            }
        }
        System.out.println(url);
    }
  ~~~