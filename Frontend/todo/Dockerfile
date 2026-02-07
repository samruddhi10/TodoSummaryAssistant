# Build the React app
FROM node:20-alpine
WORKDIR /TODO
COPY . .
RUN npm install
RUN npm run build

# Run the app using Nginx
FROM nginx:alpine
COPY --from=0 /TODO/build /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
