# 회사 제품에 RabbitMQ 추가하기

회사에 새로운 프로젝트에 투입이 되었습니다.   
새롭게 메시지큐를 사용해서 다른 모듈 사이에 메시지를 주고 받게하는 구조로 설계하였습니다.
   
### 보통의 mq
![1](https://user-images.githubusercontent.com/89080095/227427141-fd8cc6ee-afe5-4b34-911f-941cc9bad1db.PNG)


### 회사에 적용할 mq
![2](https://user-images.githubusercontent.com/89080095/227427329-91561885-8217-4c62-a96b-523d4d755cd8.PNG)

* 약간 달라지는 내용은 consumer가 동적으로 늘어날 수 있다는 점 입니다.


### 원하는 방법

consumer가 동적으로 늘어남에 따라 동적으로 rabbitMQ에 큐가 생기고 exchange에도 해당 큐에 대한 정보를 전달하고 싶었습니다.


### 해결 방법
* producer : spring boot
* rabbitmq : aws server
* consumer : spring boot

### consumer 핵심 코드
```java
package com.example.receiver.configuration;

import org.springframework.amqp.core.*;
import org.springframework.amqp.rabbit.connection.CachingConnectionFactory;
import org.springframework.amqp.rabbit.connection.ConnectionFactory;
import org.springframework.amqp.rabbit.core.RabbitTemplate;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;

import java.util.UUID;

@Configuration
public class RabbitConfig {

    @Bean
    public Queue queue() {
        String queueName = UUID.randomUUID().toString();
        String routingKey = "png-file";
        return new Queue(queueName, true, false, true);
    }
/*
    .withArgument("x-dead-letter-exchange", "myDeadLetterExchange")
    .withArgument("x-dead-letter-routing-key", "myDeadLetterQueue")
    .withArgument("x-message-ttl", 10000)
    .withArgument("x-max-length", 1000);

    queueName: 대기열 이름으로 임의의 UUID.
    durable: 대기열은 내구성이 있습니다(즉, 브로커가 다시 시작되어도 유지됨).
    exclusive: 대기열이 배타적이지 않습니다(즉, 다른 연결에서 사용할 수 있음).
    autoDelete: 대기열이 자동 삭제되지 않습니다(즉, 더 이상 소비자가 없을 때 삭제되지 않음).
    null 매개변수는 대기열이 기본 교환에 바인딩되도록 지정하는 데 사용됩니다.
    x-dead-letter-exchange: 데드 레터 메시지가 라우팅될 교환의 이름입니다.
    x-dead-letter-routing-key: 데드 레터 메시지가 라우팅될 대기열의 이름입니다.
    x-message-ttl: 대기열에 있는 메시지의 TTL(time-to-live), 밀리초 단위.
    x-max-length: 큐에 저장할 수 있는 최대 메시지 수입니다.
*/
    @Bean
    public TopicExchange exchange() {
        return new TopicExchange("png");
    }

    @Bean
    public Binding binding(Queue queue, TopicExchange exchange) {
        return BindingBuilder.bind(queue)
                .to(exchange)
                .with("*.png-file.#");
    }

    @Bean
    public ConnectionFactory connectionFactory() {
        CachingConnectionFactory connectionFactory = new CachingConnectionFactory("server-ip",5672);
        connectionFactory.setUsername("guest");
        connectionFactory.setPassword("guest");
        return connectionFactory;
    }

    @Bean
    public RabbitTemplate rabbitTemplate() {
        RabbitTemplate rabbitTemplate = new RabbitTemplate(connectionFactory());
        rabbitTemplate.setRoutingKey(queue().getName()); // Set the queue name for the rabbit template
        return rabbitTemplate;
    }

}
```
* 해당 코드는 큐를 생성할 때 UUID를 만들어서 Queue의 Name을 설정합니다.
* 메시지 바인딩을 위해서 Exchange를 어떤 것을 사용할 것인지 설정을 합니다.
* 어떤 패턴이 들어왔을 때 해당 Queue를 탈 것인지 설정을 합니다.

```java
    @RabbitListener(queues = "#{queue.name}")
    public void testUUID(byte[] binData, @Header(AmqpHeaders.CONTENT_TYPE) String contentType, @Header("file_name") String fileName) throws Exception {
    
    // Logic

    }
```
* 해당 코드를 사용하여 메시지를 받을 수 있습니다.

![3](https://user-images.githubusercontent.com/89080095/227429390-dddedfe1-394f-4e48-9aa7-1f946fe3c26b.PNG)

![4](https://user-images.githubusercontent.com/89080095/227429487-36902756-8b56-43a4-8080-f391d2f2e38d.PNG)

* rabbitmq 관리 UI에서 원하는대로 적용된 것을 확인할 수 있습니다.


