# Add 'AS builder' right here
FROM node:alpine AS builder 

WORKDIR '/app'
COPY ./package.json ./
RUN npm install
COPY . .
RUN npm run build

FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf

# Now this line will correctly find the files from the first stage
COPY --from=builder /app/build /usr/share/nginx/html