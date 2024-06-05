# Use the official Node.js image as base
FROM node:14-alpine

# Set the working directory in the container
WORKDIR /app/backend

# Copy package.json and package-lock.json to the working directory
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the backend application code to the working directory
COPY . .

# Expose port 8080 (port where Node.js server will listen)
EXPOSE 5000

# Command to start the Node.js server
CMD ["npm", "start"]


# HEALTHCHECK directive to define a health check for the container
HEALTHCHECK --interval=30s --timeout=10s --start-period=5s --retries=3 \
    CMD curl -fs http://localhost:8080/health || exit 1
