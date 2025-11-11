# Use an official Node runtime as a parent image
FROM node:18-alpine

# Set working directory
WORKDIR /usr/src/app

# Copy package files first (for better caching)
COPY package.json package-lock.json ./

# Install dependencies
RUN npm ci --production

# Copy application source
COPY . .

# If your app needs build step (e.g. TypeScript or bundler), uncomment:
# RUN npm run build

# Expose the port your app listens on (adjust if different)
EXPOSE 3000

# A simple healthcheck (adjust path/port if needed)
HEALTHCHECK --interval=30s --timeout=3s --start-period=10s \
  CMD wget -qO- http://localhost:3000/health || exit 1

# Start the app
CMD ["node", "index.js"]

