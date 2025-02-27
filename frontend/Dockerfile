# each block / stage in Dockerfile starts with FROM
FROM node:lts-alpine as builder
WORKDIR '/app'
COPY package.json .
RUN npm install
# strict copy as no need to use volumes as code doesn't change like dev env.
COPY . . 
RUN npm run build

FROM nginx
# COPY --from=builder >>> means that we copy in different phase
COPY --from=builder /app/build /usr/share/nginx/html