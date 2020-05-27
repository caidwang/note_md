
- [IoC容器](#ioc%e5%ae%b9%e5%99%a8)
  - [依赖](#%e4%be%9d%e8%b5%96)
    - [依赖注入](#%e4%be%9d%e8%b5%96%e6%b3%a8%e5%85%a5)
      - [基于构造器的依赖注入](#%e5%9f%ba%e4%ba%8e%e6%9e%84%e9%80%a0%e5%99%a8%e7%9a%84%e4%be%9d%e8%b5%96%e6%b3%a8%e5%85%a5)
      - [基于Setter的依赖注入](#%e5%9f%ba%e4%ba%8esetter%e7%9a%84%e4%be%9d%e8%b5%96%e6%b3%a8%e5%85%a5)
      - [Setter vs Constructor-arg](#setter-vs-constructor-arg)
      - [循环依赖问题](#%e5%be%aa%e7%8e%af%e4%be%9d%e8%b5%96%e9%97%ae%e9%a2%98)
    - [依赖和配置细节(标签, 嵌套数据结构)](#%e4%be%9d%e8%b5%96%e5%92%8c%e9%85%8d%e7%bd%ae%e7%bb%86%e8%8a%82%e6%a0%87%e7%ad%be-%e5%b5%8c%e5%a5%97%e6%95%b0%e6%8d%ae%e7%bb%93%e6%9e%84)
      - [xml中的集合](#xml%e4%b8%ad%e7%9a%84%e9%9b%86%e5%90%88)
      - [p空间](#p%e7%a9%ba%e9%97%b4)
      - [c空间](#c%e7%a9%ba%e9%97%b4)
    - [使用depend-on](#%e4%bd%bf%e7%94%a8depend-on)
    - [懒加载bean](#%e6%87%92%e5%8a%a0%e8%bd%bdbean)
    - [Autowire](#autowire)
    - [方法注入](#%e6%96%b9%e6%b3%95%e6%b3%a8%e5%85%a5)
      - [lookup-method](#lookup-method)
      - [任意方法的替换](#%e4%bb%bb%e6%84%8f%e6%96%b9%e6%b3%95%e7%9a%84%e6%9b%bf%e6%8d%a2)
  - [Bean的scope](#bean%e7%9a%84scope)
  - [自定义Bean的特性](#%e8%87%aa%e5%ae%9a%e4%b9%89bean%e7%9a%84%e7%89%b9%e6%80%a7)
  - [容器的扩展点](#%e5%ae%b9%e5%99%a8%e7%9a%84%e6%89%a9%e5%b1%95%e7%82%b9)
  - [基于注解的容器配置](#%e5%9f%ba%e4%ba%8e%e6%b3%a8%e8%a7%a3%e7%9a%84%e5%ae%b9%e5%99%a8%e9%85%8d%e7%bd%ae)
    - [@Component](#component)
    - [@Autowired](#autowired)
    - [@Qualifier](#qualifier)
    - [JSR330的@Inject和@Named](#jsr330%e7%9a%84inject%e5%92%8cnamed)
    - [JSR250的@Resource](#jsr250%e7%9a%84resource)
  - [classpath扫描和组件](#classpath%e6%89%ab%e6%8f%8f%e5%92%8c%e7%bb%84%e4%bb%b6)
  - [基于Java的容器配置](#%e5%9f%ba%e4%ba%8ejava%e7%9a%84%e5%ae%b9%e5%99%a8%e9%85%8d%e7%bd%ae)
  - [Environment抽象](#environment%e6%8a%bd%e8%b1%a1)
  - [注册LoadTimeWeaver](#%e6%b3%a8%e5%86%8cloadtimeweaver)
  - [ApplicationContext的额外功能](#applicationcontext%e7%9a%84%e9%a2%9d%e5%a4%96%e5%8a%9f%e8%83%bd)
  - [BeanFacotry](#beanfacotry)
- [Resources 资源抽象](#resources-%e8%b5%84%e6%ba%90%e6%8a%bd%e8%b1%a1)
- [验证, 数据绑定, 类型转换](#%e9%aa%8c%e8%af%81-%e6%95%b0%e6%8d%ae%e7%bb%91%e5%ae%9a-%e7%b1%bb%e5%9e%8b%e8%bd%ac%e6%8d%a2)
- [SpEL](#spel)
- [AOP](#aop)


# IoC容器
## 依赖
### 依赖注入
依赖注入的方式通常有**构造器参数, 工厂方法的参数或在其已经实例化之后通过set设置属性**. 在spring中这种依赖注入的手段包括了**使用xml配置, 使用annotation组件, 或使用基于Java的配置类**. 依赖注入的优点最重要的是解耦, 尤其是当依赖也是接口或抽象基类时, 更容易通过stub或mock的实现进行单元测试.

#### 基于构造器的依赖注入

构造器注入方法等价于将参数交给静态工厂方法, 通过工厂方法获得实例. 下面是一个最简单的例子.
```xml
<beans>
    <bean id="beanOne" class="x.y.ThingOne">
        <constructor-arg ref="beanTwo"/>
        <constructor-arg ref="beanThree"/>
    </bean>

    <bean id="beanTwo" class="x.y.ThingTwo"/>

    <bean id="beanThree" class="x.y.ThingThree"/>
</beans>
```
构造器注入涉及到参数解析的问题, 默认情况下根据类型进行参数解析, 如果没有冲突, 参数中的bean的定义的顺序与被注入类在实例化时构造器参数的顺序一致. 对于基本数据类型+value的注入方式, 需要显式指定参数的类型`type`, 才能够正确解析. 另一种方式是用`index`方式指明value对应的是构造器参数中的哪一个. 第三种方式是使用形参名解析, 这要求`beanOne`在编译时开启debug flag, 这样才能够保留形参名; 如果不打开这个flag, 补充方法是使用`@ConstructorProperties`注解声明参数名.

- 基于`type`解析
    ```xml
    <bean id="exampleBean" class="examples.ExampleBean">
        <constructor-arg type="int" value="7500000"/>
        <constructor-arg type="java.lang.String" value="42"/>
    </bean>
    ```
- 基于`index`解析 index从0开始
    ```xml
    <bean id="exampleBean" class="examples.ExampleBean">
        <constructor-arg index="0" value="7500000"/>
        <constructor-arg index="1" value="42"/>
    </bean>
    ```
- 基于`name`解析
    ```xml
    <bean id="exampleBean" class="examples.ExampleBean">
        <constructor-arg name="years" value="7500000"/>
        <constructor-arg name="ultimateAnswer" value="42"/>
    </bean>
    ```
- ConstructorProperties注解
    ```java
    @ConstructorProperties({"years", "ultimateAnswer"})
    public ExampleBean(int years, String ultimateAnswer) {
        //...
    }
    ```

上述方法其实是使用xml的形式向`BeanDefinition`配置了依赖, 并使用`PropertyEditor`将属性从一种格式转换成另一种.

采用静态工厂方法并采用构造器注入的例子
```xml
<bean id="exampleBean" class="examples.ExampleBean" factory-method="createInstance">
    <constructor-arg ref="anotherExampleBean"/>
    <constructor-arg ref="yetAnotherBean"/>
    <constructor-arg value="1"/>
</bean>
```

#### 基于Setter的依赖注入

```xml
<bean id="exampleBean" class="examples.ExampleBean">
    <!-- setter injection using the neater ref attribute -->
    <property name="beanTwo" ref="yetAnotherBean"/>
    <property name="integerProperty" value="1"/>
</bean>
```

#### Setter vs Constructor-arg

构造器注入的优点:
- 编程级别的参数检查
- 能够产生immutable的对象
- 返回的对象保证处于完整初始化的状态

setter注入的优点:
- 能够在初始化完对象后对其进行重配置和重注入

建议: 对必要的依赖采用构造器注入, 可选的依赖采用setter注入; Spring更加推荐构造器注入

#### 循环依赖问题
容器进行依赖解析的过程如下:
- 用描述所有beans的配置元信息(从xml, 注解, java中得到)初始化`ApplicationContext`
- bean的依赖按照属性, 构造器参数或静态工厂方法的参数形式表示, 并在bean产生的时候提供给它
- 每个属性/构造器参数实际是一个值或该容器的另一个bean
- 每个value的属性或参数都会被转换成实际类型, Spring默认情况下能够转换int, long, String, boolean等基础类型.

容器创建时会对给到它的bean的配置进行验证, 但是实际将参数给bean是在其被创建时.单例的预加载(默认)的bean会在容器创建时进行创建, 其他的会在使用时创建, 因此解析失败也可能发生在中间某个bean被第一次创建的时刻.

当使用构造器注入时, 如果发生循环依赖可能无法解决, 抛出`BeanCurrentlyInCreationException`异常. 当使用Setter注入时, 会将未完全初始化的bean注入到另一个bean, 之后采用set完成其注入.

Spring会尽可能晚的设置属性和解析依赖, 导致了可能在后期发生属性异常的问题, 这也是为什么ApplicationContext会采用预加载的策略, 在创建时产生好所有bean.

### 依赖和配置细节(标签, 嵌套数据结构)

**\<value\>标签**

value标签的属性会通过`PropertyEditor`的机制转换为实际类型的对象并注入.

在这个部分重点需要提一下的是一个xml解析的类型`java.util.Properites`, 对于支持用Propeties配置的类, xml可以通过以下形式配置Properties的内容.
```xml
<bean id="mappings"
    class="org.springframework.context.support.PropertySourcesPlaceholderConfigurer">
    <!-- typed as a java.util.Properties -->
    <property name="properties">
        <value>
            jdbc.driver.className=com.mysql.jdbc.Driver
            jdbc.url=jdbc:mysql://localhost:3306/mydb
        </value>
    </property>
</bean>
```

**\<ref\>标签**

ref标签中的值,除了按照默认的`ref="beanId"`, 还可以通过一个嵌套标签, 使用`parent`指向一个父容器中的bean, 例如, 这里accountService的bean并不是在当前容器中:
```xml
<!-- in the child (descendant) context -->
<bean id="accountService" <!-- bean name is the same as the parent bean -->
    class="org.springframework.aop.framework.ProxyFactoryBean">
    <property name="target">
        <ref parent="accountService"/> <!-- notice how we refer to the parent bean -->
    </property>
    <!-- insert other configuration and dependencies as required here -->
</bean>
```

**嵌套bean**
```xml
<bean id="outer" class="...">
    <!-- instead of using a reference to a target bean, simply define the target bean inline -->
    <property name="target">
        <bean class="com.example.Person"> <!-- this is the inner bean -->
            <property name="name" value="Fiona Apple"/>
            <property name="age" value="25"/>
        </bean>
    </property>
</bean>
```
嵌套Bean不需要指定id或name, 容器会忽略其scope, 它是匿名的, 也不会被别的bean注入.

#### xml中的集合

\<list/\>,对应Java集合中的List; \<set/\>对应Set; \<map/\> 对应Map;\<props/\> 对应Properties

```xml
<bean id="moreComplexObject" class="example.ComplexObject">
    <!-- results in a setAdminEmails(java.util.Properties) call -->
    <property name="adminEmails">
        <props>
            <prop key="administrator">administrator@example.org</prop>
            <prop key="support">support@example.org</prop>
            <prop key="development">development@example.org</prop>
        </props>
    </property>
    <!-- results in a setSomeList(java.util.List) call -->
    <property name="someList">
        <list>
            <value>a list element followed by a reference</value>
            <ref bean="myDataSource" />
        </list>
    </property>
    <!-- results in a setSomeMap(java.util.Map) call -->
    <property name="someMap">
        <map>
            <entry key="an entry" value="just some string"/>
            <entry key ="a ref" value-ref="myDataSource"/>
        </map>
    </property>
    <!-- results in a setSomeSet(java.util.Set) call -->
    <property name="someSet">
        <set>
            <value>just some string</value>
            <ref bean="myDataSource" />
        </set>
    </property>
</bean>
```

map的key或value, set的value又可以是以下标签中的任意一种
```xml
bean | ref | idref | list | set | map | props | value | null
```
但是对于强类型的集合数据类型, 例如`Map<String, Float>`, Spring会检查和转化类型. 对于null类型的value, Spring提供了`<null/>`标签.

**集合合并**

处理父子bean的属性的融合, 略


#### p空间
property标签的一种缩写形式

```xml
<beans xmlns="http://www.springframework.org/schema/beans"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xmlns:p="http://www.springframework.org/schema/p"
    xsi:schemaLocation="http://www.springframework.org/schema/beans
        https://www.springframework.org/schema/beans/spring-beans.xsd">

    <bean name="john-classic" class="com.example.Person">
        <property name="name" value="John Doe"/>
        <property name="spouse" ref="jane"/>
    </bean>

    <bean name="john-modern"
        class="com.example.Person"
        p:name="John Doe"
        p:spouse-ref="jane"/>

    <bean name="jane" class="com.example.Person">
        <property name="name" value="Jane Doe"/>
    </bean>
</beans>
```

#### c空间
constructor-arg标签的一种缩写形式

```xml
<beans xmlns="http://www.springframework.org/schema/beans"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xmlns:c="http://www.springframework.org/schema/c"
    xsi:schemaLocation="http://www.springframework.org/schema/beans
        https://www.springframework.org/schema/beans/spring-beans.xsd">

    <bean id="beanTwo" class="x.y.ThingTwo"/>
    <bean id="beanThree" class="x.y.ThingThree"/>

    <!-- traditional declaration with optional argument names -->
    <bean id="beanOne" class="x.y.ThingOne">
        <constructor-arg name="thingTwo" ref="beanTwo"/>
        <constructor-arg name="thingThree" ref="beanThree"/>
        <constructor-arg name="email" value="something@somewhere.com"/>
    </bean>

    <!-- c-namespace declaration with argument names -->
    <bean id="beanOne" class="x.y.ThingOne" c:thingTwo-ref="beanTwo"
        c:thingThree-ref="beanThree" c:email="something@somewhere.com"/>
    
    <!--对于只能用index的情况-->
    <bean id="beanOne" class="x.y.ThingOne" c:_0-ref="beanTwo" c:_1-ref="beanThree"
    c:_2="something@somewhere.com"/>
</beans>
```

### 使用depend-on
`depend-on`属性现实的要求一个或多个bean在当前bean初始化之前进行初始化. 该标签常常意味着当前bean依赖`depend-on`对应的bean, 通常这种依赖关系可以使用`ref`标签表示, 但是某些场景下, 这种bean之间的依赖没有那么直接, 比如对于一个数据库驱动, 需要一个静态的initializer.
```xml
<bean id="beanOne" class="ExampleBean" depends-on="manager1, manager2"/>
<bean id="manager" class="ManagerBean" />
```
多个bean的情形可以用逗号, 空格, 分号分隔.


### 懒加载bean

ApplicationContext默认会在初始化阶段创建和配置所有Singleton bean, 当希望懒加载某个bean时, 添加`lazy-init="true"`属性, 则bean会在第一次使用时创建和注入. 但是如果该bean是另一个非懒加载bean的注入时, 它依然会在初始化阶段被加载.
```xml
<bean id="lazy" class="com.something.ExpensiveToCreateBean" lazy-init="true"/>
<bean name="not.lazy" class="com.something.AnotherBean"/>
```

另一种声明多个bean为懒加载的方法, 给beans添加属性
```xml
<beans default-lazy-init="true">
    <!-- no beans will be pre-instantiated... -->
</beans>
```

### Autowire
优点:
- 减少了指定属性和构造器参数的需要
- 当bean的属性或构造器参数发生变化时, 可以自动适应不用修改xml

限制和缺点:
- 显示的property和constructor-arg设置会覆盖autowire. autowire不能用于原始类型, String, Class
- 不如显式声明明确
- 可能多个bean会匹配造成异常

autowiring的模式
|mode|explanation|
|-|-|
no|默认, 只能通过ref引入其他bean
byName|在容器中搜索和属性具有相同名字的bean注入
byType|根据属性的类型在容器中找到bean并注入, 容器中有多个匹配时报错
constructor| 和byType相似, 区别是作用于构造器参数

**将bean排除autowiring候选**

在xml的配置中, 对`<bean/>`添加`autowire-candidate=false`属性, 可以让这个bean不作为别的bean在autowire时考虑的bean.

**这种机制只适用于byType的模式, 当使用byName时, 即使这个bean已经设置了false依然会被另一个bean作为注入.**

对`<beans>`标签可以设置整体的策略`default-autowire-candidates`

### 方法注入
思考一种场景, 当两个scope不同的bean需要依赖时, 比如A是一个singleton的bean, 它的一个方法每次调用时,想要注入一个prototype的bean B, 但是正常的ref只会在A初始化时注入一次, 不能够达到每次调用方法新注入一个的目的.

一种可行的方法是在A的方法中使用`getBean`. 但是这种方法会造成Spring的侵入.

#### lookup-method
lookup-method提供了一种机制, 让容器重写它拥有的bean的方法, 方法返回容器持有的另一个bean, 返回的bean通常是prototype的, 其底层的技术是用CGLIB继承A这个bean的类并重写.该机制能够运行的前提:
- A不是final类, 要重写的方法不是final方法
- lookup method不能和工厂方法以及`@Bean`修饰的配置方法一起工作.
- 对于要重写的方法, 可以将其声明成一个抽象方法,结构如下
```
<public|protected> [abstract] <return-type> theMethodName(no-arguments);
```
在xml中按照如下配置
```xml
<!-- a stateful bean deployed as a prototype (non-singleton) -->
<bean id="myCommand" class="fiona.apple.AsyncCommand" scope="prototype">
    <!-- inject dependencies here as required -->
</bean>

<!-- commandProcessor uses statefulCommandHelper -->
<bean id="commandManager" class="fiona.apple.CommandManager">
    <lookup-method name="createCommand" bean="myCommand"/>
</bean>
```

基于注解的配置可以使用`@Lookup`注解, 注解的参数value为要注入的bean的name/id, 或者也可以不写, 依赖容器的解析return-type的能力返回正确的bean.

```java
public abstract class CommandManager {

    public Object process(Object commandState) {
        Command command = createCommand();
        command.setState(commandState);
        return command.execute();
    }

    @Lookup("myCommand")
    protected abstract Command createCommand();
}
```

> 同样可以访问不同scope的bean的还有`ObjectFactory/Provider`注入点.

#### 任意方法的替换
可以用一个是实现了`org.springframework.beans.factory.support.MethodReplacer`接口的类的bean替换另一个bean的某个方法

例如下面这个例子, 将替换`MyValueCaculator.computeValue`方法.

原bean和其方法
```java
public class MyValueCalculator {
    public String computeValue(String input) {
        // some real code...
    }
    // some other methods...
}
```

替换类:

```java
public class ReplacementComputeValue implements MethodReplacer {
    public Object reimplement(Object o, Method m, Object[] args) throws Throwable {
        // get the input value, work with it, and return a computed result
        String input = (String) args[0];
        ...
        return ...;
    }
}
```

xml的配置
```xml
<bean id="myValueCalculator" class="x.y.z.MyValueCalculator">
    <!-- arbitrary method replacement -->
    <replaced-method name="computeValue" replacer="replacementComputeValue">
        <arg-type>String</arg-type>
    </replaced-method>
</bean>

<bean id="replacementComputeValue" class="a.b.c.ReplacementComputeValue"/>
```
## Bean的scope

## 自定义Bean的特性

## 容器的扩展点

## 基于注解的容器配置

### @Component

`@Component`注解是`@Service`,`@Controlor`, `@Repository`的元注解, 如果不指定bean的名称, 则Spring假定bean名称与以小写字母开头的类的名称相同

使用`<context: component-scan base-package="name.of.package"/>`来指定一个用于搜索Spring bean的包列表, 该列表以逗号分隔

包扫描的参数配置, 包扫描中包含可配置的参数说明对扫描对象进行筛选, `include-filter`说明了只扫描某一些类, `exclude-filter`说明了排除某些类. 上述两个配置项包含了type和expression两个参数.

```xml
<context:component-scan base-package="sample.example">
    <context:include-filter type="annotation" expression="example.annotation.MyAnnotation"/>
    <context:exclude-filter type="regex" expression=".*Detail"/>
</context:component-scan>
```

上面举了一个参数配置的例子, 具体的type可选项包括:
|type值|描述|
|:-|:-|
annotation|expresstion特性需要指定为一个注释的完全限定类名, 表示使用了该注释的bean类会被包含或排除
assignable|expression特性需要指定为一个可以被bean类分配到的类或接口的完全限定名称
aspectj|expression特性需要指定为一个用于过滤bean类的AspectJ表达式
regex|expression特性需要指定为一个用于通过名称过滤bean类的正则表达式
custom|expression特性需要指定为一个用于过滤bean类的`org.springframework.core.type.TypeFilter`接口的实现

### @Autowired

用于**通过类型**自动装配依赖项. 在创建一个类的实例时, Spring的`AutowiredAnnotationBeanProcessor`(一种BeanPostProcessor的实现, 该后处理还会处理JSR330的@Inject注释的字段)负责自动装配类中标注了`Autowired`的字段.

使用@Autowired注释的字段不需要一定是公有的或具有相应的公有setter方法

如果一个方法使用了@Autowired注释, 则该方法的参数是自动装配的, 注意在创建bean实例之后, 将自动调用使用@Autowired注释的方法.

如果将@Autowired的required特性值设为false, 则该依赖项是可选的. 意味着如果将required特性值设置为false, 则即使在spring容器找不到匹配所需类型的bean时, 也不会抛出异常

一个bean可以定义多个@Autowired注释的构造函数, 但是所有构造函数的required属性都需要是false, 否则会报错, spring选择构造函数时, 具有最大序号且满足依赖项的构造函数将被选中.

### @Qualifier

可以使用Spring的@Qualifier注释以及@Autowired注释来按名称自动连接依赖项, 具体的做法是, Autowired先选出候选项, Qualifier再指定唯一的bean

可以通过定义一个类型化的集合来自动装配与限定符相关联的所有bean

### JSR330的@Inject和@Named

@Autowired和@Inject具有相同的语义, 用于按类型自动装配依赖项.如果在类型级别使用@Named注释, 它的作用就像@Component知识. 如果在方法参数级或构造函数参数级使用@Named注解, 作用就像@Qualifier注释

### JSR250的@Resource

该注释支持按字段和setter方法的名称自动装配. 不能用@Resource注释来自动装配构造函数参数和接受多个参数的方法.

如果使用@Autowired和@Qualifier组合来按名称执行自动装配, Spring首先根据自动装配的字段类型来查找bean,以便通过由@Qualifier注释指定的bean名称来缩小候选范围到唯一的bean. 但是如果使用@Resource注释, Spring使用其指定的bean名称来定位唯一的bean

Autowired不适用于本身为集合或Map类型的bean. 如果使用util模式的map元素定义一个bean, 则应该使用@Resource来自动装配bean

## classpath扫描和组件

## 基于Java的容器配置

## Environment抽象

## 注册LoadTimeWeaver

## ApplicationContext的额外功能

## BeanFacotry

# Resources 资源抽象

# 验证, 数据绑定, 类型转换

# SpEL

# AOP
