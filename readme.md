# 搭建这个项目的原因
* 高版本的springboot已经不支持zipkin,会报错
* zipkin也推荐用官方的jar包直接启动,不再推荐自己搭建server了
# 搭建这个项目的目的  
需要把zipkin-server注册到springcloud的场景
# 支持集成的最高版本
* springboot      2.1.x.RELEASE  
* springcloud     Greenwich.x  
* zipkin          2.12.9  
# 注意点
* 这个版本的zipkin会默认8080端口,即便你配置了`server.port = 8081`也不会生效,访问zipkin的地址http://localhost:8080/zipkin
* 这个版本的zipkin需要配置`server.compression.enabled = true`,否则启动会报错`Factory method 'armeriaServer' threw exception; nested exception is java.lang.NullPointerException`
* 实测`2.12.3`版本的zipkin不会出现上面两个问题.  
`server.port = 8081`会生效  
`server.compression.enabled = true`不配置也不会报错
* 实测`2.12.4`,`2.12.5`版本的zipkin`server.compression.enabled = true`不配置不报错,但是端口号无法指定
* 集成的`zipkin-server`和docker镜像`openzipkin/zipkin`的UI界面长得不一样  
集成的`zipkin-server`的UI界面很简陋,但功能都有    
docker镜像`openzipkin/zipkin`的UI界面看起来很好看  