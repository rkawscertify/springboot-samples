# springboot-sample-1
 
1. Sample done using 
	Spring Tool Suite 4 
	Version: 4.9.0.RELEASE
	Build Id: 202012132054
	
2. Do 'File -> New -> Spring Starter Project

3. Fill in the required details

4. Add the dependency Spring Web, follow and generate
	- @SpringBootApplication (a convenience annotation that adds @Configuration, @EnableAutoConfiguration, @ComponentScan)

5. Create a rest controller - 'HelloWorldController.java'
	- Your Controller should be in the Child package of SpringBootApplication. e.g if your SpringbootApplication main method is under com.sample.demo package then your Controller class should be under com.sample.demo.controller.
	- @RestController (combines @Controller and @ResponseBody, two annotations that results in web requests returning data rather than a view)
	- @RequestMapping("..")
	
6. Run using following and verify
	http://localhost:8080
	or
	curl localhost:8080

7. Set-up live re-load 
	- For it to work 'Project -> Build Automatically' must be selected 
	- add following to pom.xml
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-devtools</artifactId>
			<optional>true</optional>
		</dependency>
	
8. Create unit test for controller - 'HelloWorldControllerTest.java'
	- This dependency is required
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-test</artifactId>
			<scope>test</scope>
		</dependency>
	- @SpringBootTest
	- @AutoConfigureMockMvc
	- MockMvc (MockMvc comes from Spring Test and lets you, through a set of convenient builder classes, send HTTP requests into the DispatcherServlet and 	make assertions about the result.)
	- @WebMvcTest
	
9. Create integration test for controller - 'HelloWorldControllerIT.java'

10. Can run test cases either by "Run As -> JUnit Test" or "Run As - Maven Build". When running as Maven build ensure skip tests is not checked in your run configuration.

11. Add production grade services with actuator module
	- such as health, audits, beans, and more
	- This dependency is required
	<dependency>
		<groupId>org.springframework.boot</groupId>
		<artifactId>spring-boot-starter-actuator</artifactId>
	</dependency>
	- new set of RESTful end points should get added to the application
	- curl localhost:8080/actuator, curl localhost:8080/actuator/health, curl localhost:8080/actuator/info, curl -X POST localhost:8080/actuator/shutdown
	- Refer https://docs.spring.io/spring-boot/docs/2.4.2/reference/htmlsingle/#production-ready-endpoints