# configserver-example
Spring cloud config server example

To test it 
run
```shell script
mvn springboot:run
```

or via docker
```shell script
docker run --network=host cracker2709/spring-cloud-configserver-example:latest
```

Client config to set in src/main/resources/bootstrap.yml for service1 branch develop

```yaml
spring:
  application:
    name: service1
  cloud:
    config:
      uri: http://localhost:8888
      fail-fast: true
      retry:
        maxAttempts: 5
      label: develop
      name: common,${spring.application.name}
```



## Url to retrieve config is
- http://localhost:8888/common,{service}/{env}/{branch-name}

## Test common props on master branch via
- http://localhost:8888/common/dev/master
- http://localhost:8888/common/uat/master
- http://localhost:8888/common/prod/master

## Test common and service1 props on master branch via
- http://localhost:8888/common,service1/dev/master
- http://localhost:8888/common,service1/uat/master
- http://localhost:8888/common,service1/prod/master

## Test common and service2 props on master branch via
- http://localhost:8888/common,service2/dev/master
- http://localhost:8888/common,service2/uat/master
- http://localhost:8888/common,service2/prod/master

## Test common props on develop branch via
- http://localhost:8888/common/dev/develop
- http://localhost:8888/common/uat/develop
- http://localhost:8888/common/prod/develop

## Test common and service1 props on develop branch via
- http://localhost:8888/common,service1/dev/develop
- http://localhost:8888/common,service1/uat/develop
- http://localhost:8888/common,service1/prod/develop

## Test common and service2 props on develop branch via
- http://localhost:8888/common,service2/dev/develop
- http://localhost:8888/common,service2/uat/develop
- http://localhost:8888/common,service2/prod/develop
