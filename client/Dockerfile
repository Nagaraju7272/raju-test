# Stage 1: Build React app
FROM node:20-alpine AS build

WORKDIR /usr/src/app

# Copy package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy frontend source code
COPY . .

# Build React app (creates /usr/src/app/build)
RUN npm run build

# Stage 2: Serve with nginx
FROM nginx:alpine

# Copy build folder from previous stage
COPY --from=build /usr/src/app/build /usr/share/nginx/html

# Expose frontend port
EXPOSE 80

# Start nginx
CMD ["nginx", "-g", "daemon off;"]