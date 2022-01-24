```
单元测试UT
	junit: junit4.x、junit5.x
	testNG
 	mock
 		mockito + powermock 推荐使用
		easymock
		jmock
	behavior 功能测试
		concordion 主要报表相关的测试
		cucumber 推荐使用
```



```
代码扫描检查
	sonar 推荐使用
	sonar scan
```



```
How to mock
1.@RunWith(MockitoJUnitRunner.class)
2.@Rule public MockitoRule mockito = MockitoJUnit.rule()
3.MockitoAnnotations.initMocks(this);
4.Deep mock
```



```
How to stubbling
Stubbing void methods
Stubbing method with exception
Stubbing consecutive calls(iterator-style stubbing)
Stubbing with real call
Stubbing with callbacks
```

