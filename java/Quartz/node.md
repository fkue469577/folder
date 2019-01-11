## 1、核心概念

1） Job 表示一个工作，要执行的具体内容。此接口中只有一个方法，如下：

```
void execute(JobExecutionContext context) 
```

2） JobDetail 表示一个具体的可执行的调度程序，Job 是这个可执行程调度程序所要执行的内容，另外 JobDetail 还包含了这个任务调度的方案和策略。 
3） Trigger 代表一个调度参数的配置，什么时候去调。 
4） Scheduler 代表一个调度容器，一个调度容器中可以注册多个 JobDetail 和 Trigger。当 Trigger 与 JobDetail 组合，就可以被 Scheduler 容器调度了。 

## 2、Quartz API的关键接口是 

1）Scheduler - 与调度程序交互的主要API。
2）Job - 由希望由调度程序执行的组件实现的接口。
3）JobDetail - 用于定义作业的实例。
4）Trigger（即触发器） - 定义执行给定作业的计划的组件。
5）JobBuilder - 用于定义/构建JobDetail实例，用于定义作业的实例。
6）TriggerBuilder - 用于定义/构建触发器实例。

## 3、Job执行过程

​	当Job的一个trigger被触发时，execute()方法由调度程序的一个工作线程调用。传递给execute()方法的JobExecutionContext对象向作业实例提供有关其“运行时”环Job的一个trigger被出发后，execute()方法会被scheduler的一个工作线程调用；传递给execute()方法的JobExecutionContext对象中保存着该job运行时的一些信息，执行job的scheduler的引用，触发job的trigger的引用，jobDetail对应引用，以及一些其他信息。

​	JobDetail对象是在讲job加入scheduler时，有客户端程序（你的程序）创建的。它包含job的各种属性设置，以及用于存储job实例状态信息的JobDataMap。

​	Trigger用于触发Job的执行。当你准备调度一个job时，你创建一个Trigger的实例，然后设置调度相关的属性。Trigger也有一个相关联的JobDataMap，用于给Job传递一些触发现骨干的参数。Quartz自带了各种不同类型的Trigger，最常用的主要是SimpleTrigger和CronTrigger。

​	SimpleTrigger主要用于一次性执行的Job（只在某个特定的时间点执行一次），或者Job在特定的时间点执行，重复执行N次，每次执行间隔T个时间单位。CronTrigger在基于日历的调度上非常有用，如“每个星期五的正午”，或者“每月的第十天的上午10:15”等。 

​	Job被创建后，可以保存在Scheduler中，与Trigger是独立的，同一个Job可以有多个Trigger；这种松耦合的另一个好处是，当与Scheduler中的Job关联的trigger都过期时，可以配置Job稍后被重新调度，而不用重新定义Job；还有，可以修改或者替换Trigger，而不用重新定义与之关联的Job。 

## 4、Simple Trigger

概念：在具体的时间点执行一次，或者在具体的时间点执行，并且以指定的间隔重复执行若干次。比如，你有一个trigger，你可以设置它在2015年1月13日的上午11:23:54准时触发，或者在这个时间点触发，并且每隔2秒触发一次，一共重复5次。 





































