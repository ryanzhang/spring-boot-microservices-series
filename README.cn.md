# spring-boot-microservices-series
Spring Cloud coolstore 微服务实例 
## 如何运行?

### 构建 Build:

`spring-boot-microservices-series> ./mvnw clean package -DskipTests=true`

### 如何在容器中启动所有:
`docker-compose up -d`

### 关闭
`docker-compse down`

### 如何在容器中启动:

`spring-boot-microservices-series> docker-compose up -d mysqldb rabbitmq setup-vault config-server service-registry hystrix-dashboard`

**如何在本地或者容器中启动coolstore微服务程序:**

**本地:** 

`spring-boot-microservices-series/catalog-service> ./mvnw spring-boot:run`

**容器环境:** 

`spring-boot-microservices-series> docker-compose up -d <service> --build --force-recreate`

Ex: `spring-boot-microservices-series> docker-compose up -d catalog-service --build --force-recreate`


* MySQL container:
     * hostname: mysqldb
     * Ports : 3306:3306 (<host_port>:<container_port>)
     * Username/Password: root/admin

* RabbitMQ:
     * hostname: rabbitmq
     * Ports: 5672:5672, 15672:15672
     * Admin UI: http://localhost:15672
     * Username/password: guest/guest

* Vault:
    * hostname: vault
    * Ports: 8200:8200
    * Root token: 934f9eae-31ff-a8ef-e1ca-4bea9e07aa09

* config-server:
    * hostname: config-server
    * Ports: 8888:8888
    * URL: http://localhost:8888/

* service-registry:
    * hostname: service-registry
    * Ports: 8761:8761
    * URL: http://localhost:8761/
    
* hystrix-dashboard:
    * hostname: hystrix-dashboard
    * Ports: 8788:8788
    * URL: http://localhost:8788/hystrix


* catalog-service:
    * hostname: catalog-service
    * Ports: 18181:8181
    * Actuator URL: http://localhost:18181/actuator 
    * Service URL: http://localhost:18181/api/products
    * hystrix stream: http://192.168.71.174:18181/actuator/hystrix.stream (不能使用localhost)
    
* inventory-service   
    * hostname: inventory-service
    * Ports: 18282:8282
    * Actuator URL: http://localhost:18282/actuator
    * Service Endpoint: http://localhost:18282/api/inventory/P001
    
* order-service  
    * hostname: order-service
    * Ports: 18383:8383
    * Actuator URL: http://localhost:18383/actuator 
    * Service URL: http://localhost:18383/api/orders/1 
    
* shoppingcart-ui    
    * hostname: shoppingcart-ui
    * Ports: 18080:8080
    * Service URL: http://localhost:18080/ui
