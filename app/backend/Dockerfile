FROM node:18-alpine

WORKDIR /app

RUN echo '{"name":"test-backend", "version":"1.0.0", "main":"server.js", "scripts":{"start":"node server.js"}, "dependencies":{"express":"^4.18.0"}}' > package.json

RUN npm install

RUN echo 'const express = require("express"); const app = express(); app.get("/api/health", (req, res) => res.json({status: "Backend is running!", timestamp: new Date()})); app.listen(8000, "0.0.0.0", () => console.log("Backend running on port 8000"));' > server.js

EXPOSE 8000

CMD ["npm", "start"]