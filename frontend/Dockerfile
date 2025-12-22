#STAGE 1 
FROM node:20-alpine AS build

#Setting working directory
WORKDIR /app

# Copy dependencies' files
COPY package.json package-lock.json ./

# Install dependencies
RUN npm install --omit=dev

# Copy app files
COPY . .

#Build app
RUN npm run build


#STAGE 2
FROM nginx:alpine

# Copy build output to Nginx web root
COPY --from=build /app/build /usr/share/nginx/html

# React SPA usually needs this port exposed
EXPOSE 80

# Run Nginx in foreground
CMD ["nginx", "-g", "daemon off;"]