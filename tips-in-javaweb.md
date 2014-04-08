JAVA WEB开发中的注意事项
================
## Tip 1. 使用配置文件 ##
定义一个配置文件，存放需要配置的信息。假设文件名为config.properties。
``` xml
# email configuration #
system.email=267237033@qq.com
system.email.pwd=ysw6117908128

```
如何使用该配置文件？

#### 在Spring的配置文件xml中使用 ####

 1. 使用`<context:property-placeholder />`标签，加载配置文件。
    > <context:property-placeholder location="classpath:config.properties"/>
 2. 在需要的地方通过`${name}`来使用。
    <bean id="mailSender" class="org.springframework.mail.javamail.JavaMailSenderImpl">
		<property name="host" value="smtp.qq.com" />
		<property name="defaultEncoding" value="UTF-8" />
		<property name="username" value="${system.email}" />
		<property name="password" value="${system.email.pwd}" />
		<property name="javaMailProperties">
			<props>
				<prop key="mail.debug">true</prop>
				<prop key="mail.smtp.auth">true</prop>
			</props>
		</property>
	</bean>