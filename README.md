# Introduction
Welcome to Spring Microservices in Action, Chapter 3.
Chapter 3 introduces the [Spring Cloud Config](https://cloud.spring.io/spring-cloud-config/) service and how you can use it managed the configuration of your microservices. By the time you are done reading this chapter you will have built and/or deployed:

1.  A Spring Cloud Config server that is deployed as Docker container and can manage a services configuration information using a file system or GitHub-based repository.
2.  A organization service that will manage organization data used within EagleEye.
3.  A licensing service that will manage licensing data used within EagleEye.
4.  A Postgres SQL database used to hold the data for these two services.

# Software needed
1.	Apache Maven (http://maven.apache.org). I used version 3.3.9 of the Maven. I chose Maven because, while other build tools like Gradle are extremely popular, Maven is still the pre-dominate build tool in use in the Java ecosystem. All of the code examples in this book have been compiled with Java version 1.8.
2.	Docker (http://docker.com). I built the code examples in this book using Docker V1.12 and above. I am taking advantage of the embedded DNS server in Docker that came out in release V1.11. New Docker releases are constantly coming out so it's release version you are using may change on a regular basis.
3.	Git Client (http://git-scm.com). All of the source code for this book is stored in a GitHub repository. For the book, I used version 2.8.4 of the git client.

# Building the Docker Images for Chapter 3
To build the code examples for Chapter 3 as a docker image, open a command-line window change to the directory where you have downloaded the chapter 3 source code.

Run the following maven command.  This command will execute the [Spotify docker plugin](https://github.com/spotify/docker-maven-plugin) defined in the pom.xml file.  
```shell
   ./mvnw clean package docker:build
```

This is the first chapter we will have multiple Spring projects that need to be built and compiled. Running the above command at the root of the project directory will build all of the projects. If everything builds successfully you should see a message indicating that the build was successful.

# Running the services in Chapter 3

Now we are going to use docker-compose to start the actual image. To start the docker image,
change to the docker-compose directory in your chapter 3 source code. Issue the following docker-compose command:
```shell
   docker-compose -f docker/common/docker-compose.yml up -d
```

If everything starts correctly you should see a bunch of Spring Boot information fly by on standard out. At this point all of the services needed for the chapter code examples will be running.

# Check logs of running services

```shell
   docker-compose -f docker/common/docker-compose.yml logs
```

# URLs

 - http://localhost:8888/licensing-service.yml
 - http://localhost:8888/licensing-service-dev.yml
 - http://localhost:8888/licensing-service-prod.yml

 - http://localhost:8080/v1/organizations/{organizationId}/licenses/
 - http://localhost:8080/v1/organizations/e254f8c-c442-4ebe-a82a-e2fc1d1ff78a/licenses/
 - http://localhost:8080/v1/organizations/e254f8c-c442-4ebe-a82a-e2fc1d1ff78a/licenses/f3831f8c-c338-4ebe-a82a-e2fc1d1ff78a
 - http://localhost:8080/v1/organizations/e254f8c-c442-4ebe-a82a-e2fc1d1ff78a/licenses/t9876f8c-c338-4abc-zf6a-ttt1
 - http://localhost:8080/v1/organizations/442adb6e-fa58-47f3-9ca2-ed1fecdfe86c/licenses/
 - http://localhost:8080/v1/organizations/442adb6e-fa58-47f3-9ca2-ed1fecdfe86c/licenses/38777179-7094-4200-9d61-edb101c6ea84
 - http://localhost:8080/v1/organizations/442adb6e-fa58-47f3-9ca2-ed1fecdfe86c/licenses/08dbe05-606e-4dad-9d33-90ef10e334f9
