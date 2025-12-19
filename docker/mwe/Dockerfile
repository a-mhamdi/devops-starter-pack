FROM node:alpine

# Create app directory
WORKDIR /usr/src/app

# Copy package files
COPY web-app/package*.json ./

# Install dependencies
RUN npm install --only=production

# Copy app source
COPY web-app/ .

# Create non-root user
RUN adduser -S -u 1001 -G users mhamdi
RUN chown -R mhamdi:users /usr/src/app
USER mhamdi

# Expose port
EXPOSE 3000

# Start the application
CMD ["node", "server.js"]

# docker run -p 3000:3000  -it -v ./web-app:/usr/src/app web-app:demo /bin/sh