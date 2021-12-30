SPRING CLOUD
============



## Consul integration

By Default client load balancing attempts to route requests to any of the service instances, without considering the actual status

To access only to service instances that passes the healthcheck, add in the *application.yml*. 

```
spring:
    cloud:
       consul:
          discovery:
             queryPassing: true 
```
             

More details in the source of [ConsulDiscoveryClient](https://github.com/spring-cloud/spring-cloud-consul/blob/main/spring-cloud-consul-discovery/src/main/java/org/springframework/cloud/consul/discovery/ConsulDiscoveryClient.java)




## Tip: services vertical scaling

Application name and instance id must be unique

Quick and dirty workaround


Main
```
public static void main(String[] args) {
	System.setProperty("myProcessId", ManagementFactory.getRuntimeMXBean().getName());
    SpringApplication.run(EdgeMain.class, args);
}
```

application.yml
```
spring:
  application:
    name: edge
    instance_id: ${myProcessId}
```
