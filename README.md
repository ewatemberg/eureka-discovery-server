# Eureka Discovery Server
Qué es y para qué sirve Spring Cloud Netflix Eureka?
La transición desde un entorno monolítico a otro basado en microservicios proporciona muchos beneficios desde el punto de vista del desarrollo y mantenimiento del software. Sin embargo, al mismo tiempo su adopción conlleva la aparición de una serie de problemas que necesitan ser tratados correctamente. Uno de estos "nuevos" problemas es precisamente la gestión de las direcciones de todos los microservicios de los que consta nuestra aplicación. Dependiendo del número de microservicios, así como de las políticas de replicación de los mismos, el mantenimiento de las direcciones puede llegar a ser muy complejo.
Para lidiar con esta situación, en entornos distribuidos existe un concepto denominado Servicio de registro y descubrimiento. La aplicación de dicho concepto implica la creación de un servicio cuya única tarea es mantener el registro de todos los microservicios que son desplegados o eliminados. Podríamos considerarlo como una guía de teléfonos que contiene las direcciones de los microservicios. Para facilitarnos le implementación de dicho servicio Spring Cloud nos ofrece el componente Spring Cloud Netflix Eureka.

### Cómo funciona Spring Cloud Netflix Eureka?

Eureka es un servicio rest que permite al resto de microservicios registrarse en su directorio. Esto es muy importante, puesto que no es Eureka quien registra los microservicios, sino los microservicios los que solicitan registrarse en el Eureka.
Cuando un microservicio registrado en Eureka arranca, envía un mensaje a Eureka indicándole que está disponible. El servidor Eureka almacenará la información de todos los microservicios registrados así como su estado. La comunicación entre cada microservicio y el servidor Eureka se realiza mediante heartbeats cada X segundos. Si Eureka no recibe un heartbeat de un determinado pasados 3 intervalos, el microservicio será eliminado del registro. Además de llevar el registro de los microservicios activos, Eureka también ofrece al resto de microservicios la posibilidad de "descubrir" y acceder al resto de microservicios registrados. Por ello Eureka es considerado un servicio de registro y descubrimiento de miscroservicios


Antes de seguir vamos a comprobar que nuestro servicio [EchoService](https://github.com/ewatemberg/eureka-client-microservice) se ha registrado correctamente en nuestro servidor Eureka. Para ello arrancamos (por este orden) nuestros servicios: [Spring Cloud Config](https://github.com/ewatemberg/spring-cloud-configuration-server-example), [Eureka, Gateway Zuul](https://github.com/ewatemberg/zuul-gateway-server) y por último [EchoService](https://github.com/ewatemberg/eureka-client-microservice). Una vez arrancados todos sin errores, al acceder a la interfaz web de Eureka veremos los servicios registrados Zuul y EchoService tal y como muestra la siguiente imagen.

![alt text](https://github.com/ewatemberg/eureka-discovery-server/blob/master/doc/img/eureka.png)


![alt text](https://github.com/ewatemberg/eureka-discovery-server/blob/master/doc/img/java-microservices-with-netflix-oss-spring.jpg)

### Related
* [Spring Cloud Config](https://github.com/ewatemberg/spring-cloud-configuration-server-example)
* [Repositorio Configuración Centralizada](https://github.com/ewatemberg/spring-cloud-configuration-repository)
* [Servicio Gateway mediante Zuul](https://github.com/ewatemberg/zuul-gateway-server)
* [Microservicio Echo](https://github.com/ewatemberg/eureka-client-microservice)

#### Fuente:
[Miguel Doctor Yuste](https://medium.com/@migueldoctor/spring-cloud-series-crea-un-servicio-de-registro-y-descubrimiento-con-spring-cloud-netflix-eureka-4758615ad4cb)
