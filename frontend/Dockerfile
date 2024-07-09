
# Use the official node image as a base
FROM node:18 as build

# Set working directory
WORKDIR /app

COPY . /app
# Install dependencies
# COPY package.json package-lock.json ./
RUN npm install 

# Copy all files and build the app

# RUN npm run build



# Serve the app with nginx
# FROM nginx:alpine
# COPY --from=build /app/dist /usr/share/nginx/html

# Expose port 80

EXPOSE 5173

# Start nginx
CMD ["npm", "run", "dev", "--", "--host" ]
