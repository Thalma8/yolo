# Stage 1: Build the app using full Node.js image
FROM node:14 AS build

# Set working directory
WORKDIR /usr/src/app

# Copy package files and install dependencies
COPY package*.json ./


# Copy the entire app
COPY . .

# Stage 2: Create a lightweight production image with Node.js and npm
FROM node:14-alpine

# Set working directory
WORKDIR /app

# Copy built app from previous stage
COPY --from=build /usr/src/app /app

# Expose the backend port
EXPOSE 5000

# Run the app
CMD ["node", "server.js"]
