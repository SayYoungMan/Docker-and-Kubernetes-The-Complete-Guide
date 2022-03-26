FROM node:16-alpine as builder
WORKDIR "/app"
COPY ["7. Continuous Integration and Deployment with AWS/frontend/package.json", "."]
RUN npm install
ADD ["7. Continuous Integration and Deployment with AWS/frontend", "./"]
RUN npm run build

FROM nginx
EXPOSE 80
COPY --from=builder /app/build /usr/share/nginx/html