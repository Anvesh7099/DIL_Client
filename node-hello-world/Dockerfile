# Base image
FROM node:18

# Set working directory inside container
WORKDIR /app

# Copy package.json & install deps
COPY package*.json ./
RUN npm install

# Copy rest of the project files
COPY . .

# Expose port your app uses (e.g., 3000)
EXPOSE 3000

# Start the app
CMD ["npm", "start"]
