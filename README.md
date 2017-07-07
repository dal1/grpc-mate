gRPC-Mate - An enterprise ready micro service project base on [gRPC-Java](https://github.com/grpc/grpc-java)
========================================
gRPC-Mate demostrate best practice for gRPC based micro service.

* Grpc features
  * Simple RPC
  * Server streaming
  * Client streaming
  * Bi-directional streaming
  * Authentication
* Promethues integration
* Kubernetes Deployment
* [Gradle multiple builds best practice](#gradle-best-practice)
* Mockito best practice
* TestNG best practice
* Guice best practice
* Docker-Java best practice
* Protobuffer best practice 
  * use Protobuffer message as value object
  * use Protobuffer message to persist into Elasticsearch
* Quality Control best practice
  * CheckStyle
  * FindBug
  * PMD

### Demo  Script
the project will demostrate an online store search service including

* Create elasticsearch index with alias
* Uploading products into Elasticsearch (client streaming)
* Downloading products from Elasticsearch (server streaming)
* Search products from elasticsearch (simple RPC)
* Calculate products score (bi-directional streaming)

### Gradle Best Practice
* add gradle wrapper, so that it can be run anywhere

```
task wrapper(type: Wrapper) {
    gradleVersion = '4.0'
}

> gradle wrapper
```
* remove auto generated classes in clean task

```groovy
clean {
    doLast {
        // remove auto-generated files on clean
        delete "${projectDir}/src/generated"
    }
}
```
* we force gradle to detect version conflict on build

```groovy
subprojects {
    apply plugin: 'java'

    configurations.all {
        resolutionStrategy {
            // fail eagerly on version conflict (includes transitive dependencies)
            // e.g. multiple different versions of the same dependency (group and name are equal)
            failOnVersionConflict()
        }
    }
}
```
 

 