# Use an official node runtime as a parent image
FROM node:16

# Set the working directory in the container
WORKDIR /app

# Copy the package.json file into the container
COPY package.json ./

# Install any needed packages
RUN npm install

# Copy the rest of the application code into the container
COPY . .

# Build the app for production with minification
RUN npm run build

# Serve the app with a static server
# Install serve globally
RUN npm install -g serve

# Command to run the app
CMD ["serve", "-s", "build"]

# Make port 3000 available to the world outside this container
EXPOSE 3000
