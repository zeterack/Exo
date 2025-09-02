# Exercise 5 Solutions

## 1. ✅ Nginx Web Server
- **Image**: `my-nginx`
- **Port**: 8080 → 80
- **URL**: http://localhost:8080
- **Status**: Running ✅

### Commands:
```bash
cd nginx/
sudo docker build -t my-nginx .
sudo docker run -d -p 8080:80 --name nginx-test my-nginx
```

## 2. ✅ Tomcat WAR Deployment  
- **Image**: `my-tomcat` 
- **Port**: 8081 → 8080
- **URL**: http://localhost:8081/sample/
- **Status**: Running ✅

### Commands:
```bash
cd tomcat/
sudo docker build -t my-tomcat .
sudo docker run -d -p 8081:8080 --name tomcat-test my-tomcat
```

## 3. 🚧 Spring Boot Application (TODO)
Still need to:
- Clone the Spring Boot project
- Create Maven-based Dockerfile
- Compile and package the JAR
- Run the Spring Boot application

## 4. 🚧 Nginx with Pre-action (TODO)
Still need to:
- Use `nginx:alpine-slim`
- Download ifconfig.me content at startup
- Install curl/wget with Alpine package manager (apk)
- Create startup script

## 5. 🚧 Smallest Possible Image (TODO)
Challenge: Create image < 170Ki

## Current Container Status:
```bash
sudo docker ps
```

## Stop all containers:
```bash
sudo docker stop nginx-test tomcat-test
sudo docker rm nginx-test tomcat-test
```
