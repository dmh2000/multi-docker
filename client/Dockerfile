# ---------------------------------------
# PHASE 1 : build
# ---------------------------------------
# base image
FROM node:latest 

# working directory
WORKDIR /app

# setup
COPY ./package.json ./
RUN npm install

# files
COPY . .

# startup command
RUN npm run build

# ---------------------------------------
# PHASE 2 : run
# ---------------------------------------
#base
FROM nginx:latest

# publish port
EXPOSE 3000

# files
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=0 /app/build /usr/share/nginx/html