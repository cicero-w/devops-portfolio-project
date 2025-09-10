FROM node:18-alpine AS builder

WORKDIR /app

COPY package*.json ./

RUN npm ci --only=production

COPY . .

RUN npm run build

FROM nginx:alpine

COPY --from=builder /app/dist /usr/share/nginx/html

RUN echo 'server { \
  listen 3000; \
  server_name localhost; \
  root /usr/share/nginx/html; \
  index index.html; \
  location / { \
  try_files $uri $uri/ /index.html; \
  } \
  location /api/ { \
  proxy_pass http://backend:8000; \
  } \
  }' > /etc/nginx/conf.d/default.conf

RUN rm /etc/nginx/conf.d/default.conf.bak 2>/dev/null || true

EXPOSE 3000

RUN sed -i 's/listen       80;/listen       3000;/' /etc/nginx/conf.d/default.conf 2>/dev/null || true

CMD ["nginx", "-g", "daemon off;"]