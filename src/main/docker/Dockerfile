# 指定基础镜像,需要在运行程序的机器上配置hosts文件，指定registry.eversec.com对应ip
FROM registry.eversec.com:5000/centos-jre:8-20210222
# 实现挂载功能，将本地文件夹或者其它容器中的文件夹挂在到这个容器中
VOLUME /app/tmp
# 复制命令，config、jar、lib，需要pom中配置，1、<build>下配置resources，2、<build>下<plugin>下<configuration>下配置<resources>
ADD config /app/config
ADD gateway-0.0.1-SNAPSHOT.jar /app/gateway.jar
ADD lib /app/lib
# 运行指定的命令
RUN sh -c 'touch /app/gateway.jar'
# 设置环境变量
ENV JAVA_OPTS=""
# 设置工作目录，对RUN,CMD,ENTRYPOINT,COPY,ADD生效。如果不存在则会创建，也可以设置多次
WORKDIR /app
# 启动时的默认命令
ENTRYPOINT ["sh", "-c", "java $JAVA_OPTS -Djava.security.egd=file:/dev/./urandom -jar gateway.jar"]