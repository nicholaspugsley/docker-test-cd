# Dockerfile
# Stage 1 - the build process
FROM node:15.4.0-alpine as build-deps
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

# Stage 2 - the production environment
FROM node:15.4.0-alpine
WORKDIR /app
COPY --from=build-deps /app/.next ./.next
COPY --from=build-deps /app/node_modules ./node_modules
COPY --from=build-deps /app/public ./public
COPY package*.json ./
EXPOSE 3000
CMD ["npm", "start"]
