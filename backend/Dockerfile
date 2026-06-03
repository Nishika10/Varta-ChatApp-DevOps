# Stage 1: Build stage to install dependencies
FROM node:18-alpine AS builder
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .

# Stage 2: Run stage to keep the final image small
FROM node:18-alpine
WORKDIR /app
COPY --from=builder /app ./

EXPOSE 5001
CMD ["node", "src/index.js"]