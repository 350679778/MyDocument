```go
<!-- 让spring管理sqlsessionfactory 使用mybatis和spring整合包中的 -->
<bean id="sqlSessionFactory" class="org.mybatis.spring.SqlSessionFactoryBean">
	<!-- 数据库连接池 -->
	<property name="dataSource" ref="dataSource" />
	<!-- 加载mybatis的全局配置文件 -->
	<property name="configLocation" value="classpath:sqlMapConfig.xml" />
	<!-- <property name="mapperLocations" value="classpath:dao/*.xml"/> -->
</bean>
<bean class="org.mybatis.spring.mapper.MapperScannerConfigurer">
	<property name="basePackage" value="dao" />
</bean>
```
如果Mapper.xml与Mapper.class在同一个包下且同名，spring扫描Mapper.class的同时会自动扫描同名的Mapper.xml并装配到Mapper.class。
如果Mapper.xml与Mapper.class不在同一个包下或者不同名，就必须使用配置mapperLocations指定mapper.xml的位置。
此时spring是通过识别mapper.xml中的 <mapper namespace="com.fan.mapper.UserDao"> namespace的值来确定对应的Mapper.class的。
