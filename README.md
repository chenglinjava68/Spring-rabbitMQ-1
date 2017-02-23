# Spring-rabbitMQ
  在业务逻辑的异步处理，系统解耦，分布式通信以及控制高并发的场景下，消息队列有着广泛的应用。本项目基于Spring的AMQP模块，整合流行的开源消息队列中间件rabbitMQ,实现一个向rabbitMQ添加和读取消息的功能。并比较了两种模式：生产者-消费者模式和发布-订阅模式的区别。AMQP作为比JMS更加高级的消息协议，支持更多的消息路由和消息模式。
  
包含的特性如下：

  ![输入图片说明](https://github.com/shenzhanwang/Spring-rabbitMQ/blob/master/%E6%88%AA%E5%9B%BE/1.png"生产者消费者模型")
1.如上图，生产者消费者模型：添加了一个队列，并创建了两个消费者用于监听队列消息，我们发现，当有消息到达时，两个消费者会交替收到消息。这一过程虽然不用创建交换机，但会使用默认的交换机，并用默认的直连（default-direct）策略连接队列；
  ![输入图片说明](https://github.com/shenzhanwang/Spring-rabbitMQ/blob/master/%E6%88%AA%E5%9B%BE/3.png"")

2.如下图，发布订阅模型，添加两个队列，分别各用一个消费者监听，设置一个交换机，类型为广播（fanout），交换机会将收到的消息广播给所有相连的队列：

![输入图片说明](https://github.com/shenzhanwang/Spring-rabbitMQ/blob/master/%E6%88%AA%E5%9B%BE/2.png"发布订阅模型")
![输入图片说明](https://github.com/shenzhanwang/Spring-rabbitMQ/blob/master/%E6%88%AA%E5%9B%BE/8.png"在这里输入图片标题")
![输入图片说明](https://github.com/shenzhanwang/Spring-rabbitMQ/blob/master/%E6%88%AA%E5%9B%BE/4.png"fanout路由模型")

3.进入http://localhost:8080/Spring-rabbitMQ/demo 可向rabbitMQ发送消息，如下图：
![输入图片说明](https://github.com/shenzhanwang/Spring-rabbitMQ/blob/master/%E6%88%AA%E5%9B%BE/7.png"fanout路由模型")

 



