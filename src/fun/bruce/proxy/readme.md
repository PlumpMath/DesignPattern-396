### 没有理解代理模式  *2017-2-10*

#### 代理模式的分类
- 远程代理：为不同地理的对象，提供局域网代表对象
- 虚拟代理： 根据需要将资源消耗很大的对象进行延迟，真正需要的时候进行创建
- 保护代理： 权限控制
- 智能引用代理： 对目标对象提供额外的服务

#### 静态代理
*代理和被代理对象在代理之前是确定的。他们都实现相同的接口或者集成相同的抽象类。*
- 继承方式（不推荐）
- 聚合方式

#### 动态代理
- jdk动态代理 InvocationHandle
    1. 创建一个实现接口InvocationHandle的类，必须实现invoke()方法
    2. 创建被代理的类和接口
    3. 调用Proxy的静态方法，创建一个代理类newProxyInstance(ClassLoader loader,Class[] interfaces,InvocationHandle handle)
    4. 通过代理调用方法
    
- cglib动态代理 MethodInterceptor

#### JDK动态代理实现原理
    思路：通过Proxy的newProxyInstance返回代理对象
        1. 声明一段源码（动态产生代理）
        2.编译源码(jdk compiler api),产生新的类（代理类）
        3.将这个类load到内存中，产生一个新的对象（代理对象）
        4.return代理对象