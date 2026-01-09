# -------- Stage 1: Build --------
FROM node:18-alpine AS builder

WORKDIR /app

# Copy package files
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy source code
COPY . .

# Build Next.js app
RUN npm run build

# -------- Stage 2: Runtime --------
FROM node:18-alpine

WORKDIR /app

# Copy build output and node_modules from builder
COPY --from=builder /app ./

# Expose frontend port
EXPOSE 3000

# Start Next.js
CMD ["npm", "run", "start"]
