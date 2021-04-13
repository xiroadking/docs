## SpringMVC执行流程

* 用户发送请求至前端控制器DispatcherServlet；
* DispatcherServlet收到请求后，调用HandlerMapping处理器映射器，请求获取Handle；
* 处理器映射器根据请求url找到具体的处理器，生成处理器对象及处理器拦截器(如果有则生成)一并返回
* DispatcherServlet；
* DispatcherServlet 调用 HandlerAdapter处理器适配器；
* HandlerAdapter 经过适配调用 具体处理器(Handler，也叫后端控制器)；
* Handler执行完成返回ModelAndView；
* HandlerAdapter将Handler执行结果ModelAndView返回给DispatcherServlet；
* DispatcherServlet将ModelAndView传给ViewResolver视图解析器进行解析；
* ViewResolver解析后返回具体View；
* DispatcherServlet对View进行渲染视图（即将模型数据填充至视图中）
* DispatcherServlet响应用户。

![img](SpringMVC%E6%89%A7%E8%A1%8C%E6%B5%81%E7%A8%8B.png)