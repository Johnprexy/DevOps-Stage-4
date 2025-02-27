FROM node:12-alpine

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .
RUN npm run build

# Install serve to run the application
RUN npm install -g serve

EXPOSE 8080
CMD ["serve", "-s", "dist", "-l", "8080"]