FROM node:18-alpine AS builder

WORKDIR /app

COPY package*.json ./

RUN npm ci --only=production

RUN npm ci

COPY . .

RUN npm run build

FROM nginx:alpine

COPY --from=builder /app/dist /usr/share/nginx/html

RUN echo 'server { \
  listen 3000; \
  server_name localhost; \
  root /usr/share/nginx/html; \
  index index.html; \
  \
  location / { \
  try_files $uri $uri/ /index.html; \
  } \
  \
  location ~* \.(js|css|png|jpg|jpeg|gif|ico|svg)$ { \
  expires 1y; \
  add_header Cache-Control "public, immutable"; \
  } \
  }' > /etc/nginx/conf.d/default.conf

RUN rm /etc/nginx/conf.d/default.conf.dpkg-old 2>/dev/null || true

EXPOSE 3000

RUN sed -i 's/listen\s*80;/listen 3000;/g' /etc/nginx/conf.d/default.conf

CMD ["nginx", "-g", "daemon off;"]