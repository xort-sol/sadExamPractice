# Stage 1: Build frontend
FROM node:14-alpine as build

# Set the working directory in the container
WORKDIR /app/fronted

# Copy package.json and package-lock.json to the working directory
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the frontend application code to the working directory
COPY . .

# Build the frontend application
RUN npm run build

# Stage 2: Serve frontend using NGINX
FROM nginx:alpine

# Copy build files from the previous stage to NGINX directory
COPY --from=build /app/fronted/build /usr/share/nginx/html

# Expose port 80
EXPOSE 80
