# Stage 1
FROM node:8 as react-build
WORKDIR /app
COPY . ./
RUN npm install
RUN npm run build
RUN pwd && ls -al

# Stage 2 - the production environment
FROM nginx:alpine
# COPY nginx.conf /etc/nginx/conf.d/default.conf
WORKDIR /usr/share/nginx/html
COPY --from=react-build /app/build ./
EXPOSE 80
ENTRYPOINT [ "/bin/sh", "-c" ]
CMD ["nginx", "-g", "daemon off;"]

# FROM nginx:alpine
# WORKDIR /app
# COPY . ./
# RUN npm install
# RUN npm run build
# COPY ./build /usr/share/nginx/html
# EXPOSE 80
# CMD [“nginx”, “-g”, “daemon off;”]

