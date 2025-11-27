# # Stage 1: Build with Maven and Java 21
# FROM maven:3.9.6-eclipse-temurin-21 AS build
# WORKDIR /app
# COPY . .
# RUN mvn clean package -DskipTests

# # Stage 2: Run with Tomcat
# FROM tomcat:9.0-jdk17-temurin
# RUN rm -rf /usr/local/tomcat/webapps/*

# # Copy backend WAR to Tomcat
# COPY --from=build /app/target/*.war /usr/local/tomcat/webapps/ROOT.war

# EXPOSE 8080
# CMD ["catalina.sh", "run"]
# Step 1: Build the application
FROM maven:3.8.8-eclipse-temurin-17 AS build
WORKDIR /app
COPY . .
RUN mvn clean package -DskipTests

# Step 2: Run the application
FROM eclipse-temurin:17-jdk
WORKDIR /app
COPY --from=build /app/target/springapp1.war app.war

EXPOSE 9096

ENTRYPOINT ["java", "-jar", "app.war"]
