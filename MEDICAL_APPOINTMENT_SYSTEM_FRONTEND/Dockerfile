# # Step 1: Build stage (Vite app build)
# FROM node:18 AS build-stage
# WORKDIR /app
# COPY package*.json ./
# RUN npm install
# COPY . .
# RUN npm run build

# # Step 2: Runtime stage (Tomcat for serving frontend)
# FROM tomcat:9-jdk17
# RUN rm -rf /usr/local/tomcat/webapps/*

# # Copy Vite build output into Tomcat
# COPY --from=build-stage /app/dist /usr/local/tomcat/webapps/ROOT

# EXPOSE 8080
# CMD ["catalina.sh", "run"]
# Step 1: Build the frontend
FROM node:18 AS build
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

# Step 2: Serve with Nginx
FROM nginx:alpine
COPY --from=build /app/dist /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
