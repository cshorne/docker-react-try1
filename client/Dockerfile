# This is creating a builder image that is later discarded
FROM node:alpine as builder
WORKDIR '/app'
COPY package.json .
RUN npm install
COPY . .
RUN npm run build

# The folder that we care about during the run phase is /app/build
# Note that the nginx image will automatically start the nginx process
FROM nginx
COPY --from=builder /app/build /usr/share/nginx/html
