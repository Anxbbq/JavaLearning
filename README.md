# JavaLearning
video &amp; doc for java learning (collect from web)

Collections in Java
--------
[video](https://www.bilibili.com/video/BV1zD4y1Q7Fw) [doc](https://lazydog036.gitee.io/2020/10/29/JAVA%E9%9B%86%E5%90%88%E6%A1%86%E6%9E%B6/)(2020)

Spring5 IDEA version
--------
[video](https://www.bilibili.com/video/BV1WE411d7Dv) [doc](https://www.docs4dev.com/docs/zh/spring-framework/5.1.3.RELEASE/reference/)(2019)

Java8 API
-------
[video](https://www.bilibili.com/video/BV1ut411g7E9) [doc](https://blog.csdn.net/weixin_45225595/article/details/106203264)(2019)

IOC & DI
---------
[doc](https://blog.csdn.net/bestone0213/article/details/47424255)

2021/7/21
------
@JsonProperty 此注解用于属性上，作用是把该属性的名称序列化为另外一个名称，如把trueName属性序列化为name，@JsonProperty("name")  

@ConditionalOnProperty，这个注解能够控制某个configuration是否生效。具体操作是通过其两个属性name以及havingValue来实现的，其中name用来从application.properties中读取某个属性值，如果该值为空，则返回false;如果值不为空，则将该值与havingValue指定的值进行比较，如果一样则返回true;否则返回false。如果返回值为false，则该configuration不生效；为true则生效.  

@JmsListener(destination = "")  
destination：消息被寻址、发送以及接收的对象  

ObjectMapper  
```java
public static ObjectMapper mapper = new ObjectMapper();

static {
    // 转换为格式化的json
    mapper.enable(SerializationFeature.INDENT_OUTPUT);

    // 如果json中有新增的字段并且是实体类类中不存在的，不报错
    mapper.configure(DeserializationFeature.FAIL_ON_UNKNOWN_PROPERTIES, false);
}


public void testObj() throws JsonGenerationException, JsonMappingException, IOException {
    XwjUser user = new XwjUser(1, "Hello World", new Date());

    mapper.writeValue(new File("D:/test.txt"), user); // 写到文件中
    // mapper.writeValue(System.out, user); //写到控制台

    String jsonStr = mapper.writeValueAsString(user);
    System.out.println("对象转为字符串：" + jsonStr);

    byte[] byteArr = mapper.writeValueAsBytes(user);
    System.out.println("对象转为byte数组：" + byteArr);

    XwjUser userDe = mapper.readValue(jsonStr, XwjUser.class);
    System.out.println("json字符串转为对象：" + userDe);

    XwjUser useDe2 = mapper.readValue(byteArr, XwjUser.class);
    System.out.println("byte数组转为对象：" + useDe2);
}
```


