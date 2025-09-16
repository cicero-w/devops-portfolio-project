FROM node:20-alpine3.20 AS builder

LABEL maintainer="paul.antonenko.w@gmail.com"
LABEL version="1.0"
LABEL description="GitOps & DevOps: From Code to Kubernetes on macOS"

RUN apk add --no-cache curl

WORKDIR /app

COPY package*.json ./

RUN npm ci && \
  npm cache clean --force

COPY . .

RUN npm run build

FROM nginx:1.26-alpine3.21 AS production

COPY --from=builder /app/dist /usr/share/nginx/html
COPY nginx.conf /etc/nginx/conf.d/default.conf

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