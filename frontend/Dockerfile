FROM node:18 as build

WORKDIR /app
COPY . .
RUN npm install
RUN npm run build --configuration production 
RUN ls -la

# Serve phase
FROM nginx:alpine
COPY --from=build /app/dist/frontend /usr/share/nginx/html

EXPOSE 3000

CMD ["nginx", "-g", "daemon off;"]
