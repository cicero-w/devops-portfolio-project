FROM nginx:alpine

RUN echo '<!DOCTYPE html><html><head><title>DevOps Portfolio</title><style>body{font-family:Arial;text-align:center;margin-top:50px;background:#f0f8ff}h1{color:#2c3e50}.container{max-width:800px;margin:0 auto;padding:20px}.status{background:#27ae60;color:white;padding:10px;border-radius:5px;margin:20px 0}</style></head><body><div class="container"><h1>🚀 DevOps Portfolio Project</h1><div class="status">✅ Frontend is running!</div><h2>Architecture:</h2><p>📱 Frontend (Nginx) → 🔀 Reverse Proxy → ⚙️ Backend API</p><button onclick="fetch(\"/api/health\").then(r=>r.json()).then(d=>document.getElementById(\"api-status\").innerHTML=JSON.stringify(d,null,2)).catch(e=>document.getElementById(\"api-status\").innerHTML=\"❌ API Error: \"+e)">Test Backend API</button><pre id="api-status" style="background:#ecf0f1;padding:10px;border-radius:5px;margin-top:20px;text-align:left"></pre></div></body></html>' > /usr/share/nginx/html/index.html

EXPOSE 3000

RUN sed -i 's/listen       80;/listen       3000;/g' /etc/nginx/conf.d/default.conf
