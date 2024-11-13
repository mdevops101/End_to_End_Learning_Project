# Step 1: Use official Node.js image as a base image for building the app
FROM node:16 AS build

# Step 2: Set working directory in the container
WORKDIR /app

# Step 3: Copy package.json and package-lock.json (if available)
COPY package.json /app/

# Step 4: Install dependencies
RUN npm install

# Step 5: Copy the rest of the project files
COPY . /app/

# Step 6: Build the React app (Production-ready static files)
RUN npm run build

# Step 7: Use Nginx to serve the build folder on port 3000
FROM nginx:alpine

# Step 8: Expose port 3000
EXPOSE 3000

# Step 9: Copy build folder to Nginx's HTML directory
COPY --from=build /app/build /usr/share/nginx/html

# Step 10: Update Nginx config to listen on port 3000
RUN echo "server { listen 3000; location / { root /usr/share/nginx/html; try_files \$uri /index.html; } }" > /etc/nginx/conf.d/default.conf

# Step 11: Start Nginx
CMD ["nginx", "-g", "daemon off;"]

