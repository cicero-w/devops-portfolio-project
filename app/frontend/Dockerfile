FROM node:18-alpine AS builder

LABEL maintainer="paul.antonenko.w@gmail.com"
LABEL version="1.0"
LABEL description="GitOps & DevOps: From Code to Kubernetes on macOS"

RUN apk add --no-cache curl

WORKDIR /app

COPY package*.json ./

RUN npm ci --only=production && \
  npm cache clean --force

COPY . .

RUN npm run build

FROM nginx:1.25-alpine AS production

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
  etag off; \
  } \
  \
  add_header X-Frame-Options "DENY" always; \
  add_header X-Content-Type-Options "nosniff" always; \
  add_header X-XSS-Protection "1; mode=block" always; \
  \
  gzip on; \
  gzip_types text/plain text/css application/json application/javascript text/xml application/xml application/xml+rss text/javascript; \
  \
  location /health { \
  access_log off; \
  return 200 "healthy\\n"; \
  add_header Content-Type text/plain; \
  } \
  }' > /etc/nginx/conf.d/default.conf

HEALTHCHECK --interval=30s --timeout=3s --start-period=5s --retries=3 \
  CMD curl -f http://localhost:3000/health || exit 1

RUN chown -R nginx:nginx /usr/share/nginx/html && \
  chown -R nginx:nginx /var/cache/nginx && \
  chown -R nginx:nginx /var/log/nginx && \
  chown -R nginx:nginx /etc/nginx/conf.d && \
  touch /var/run/nginx.pid && \
  chown -R nginx:nginx /var/run/nginx.pid

EXPOSE 3000

USER nginx

CMD ["nginx", "-g", "daemon off;"]