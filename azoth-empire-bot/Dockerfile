ARG NODE_ENV=production

#Builder stage
FROM node:current-bullseye-slim as builder
ENV NODE_ENV=${NODE_ENV}
WORKDIR /app

COPY package*.json ./
RUN npm ci

# Final stage/image
FROM node:current-bullseye-slim
ENV NODE_ENV=${NODE_ENV}
WORKDIR /app

COPY --from=builder /app/node_modules node_modules

COPY . .

CMD ["npm", "start"]
