FROM node:20-alpine AS build
WORKDIR /app

COPY package*.json ./
COPY apps/api/package*.json apps/api/
COPY apps/web/package*.json apps/web/
RUN npm ci

COPY . .
RUN npm --workspace apps/api run build

FROM node:20-alpine
WORKDIR /app
ENV NODE_ENV=production

COPY package*.json ./
COPY apps/api/package*.json apps/api/
COPY apps/web/package*.json apps/web/
RUN npm ci --omit=dev

COPY --from=build /app/apps/api/dist ./dist
EXPOSE 3000
CMD ["node", "dist/main.js"]
