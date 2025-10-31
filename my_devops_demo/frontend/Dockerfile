# ------------------------------
# STAGE 1: Build the Vue frontend
# ------------------------------
FROM node:18-alpine AS build-stage

# Set working directory
WORKDIR /app

# Copy package.json and package-lock.json
# (Important for deterministic builds and npm ci)
COPY package*.json ./

# Install dependencies (allow older peer deps if needed)
RUN npm ci --legacy-peer-deps

# Copy all source files
COPY . .

# Set environment variable for production build
ARG FRONTEND_ENV=production
ENV VUE_APP_ENV=${FRONTEND_ENV}

# Build the production-ready files
RUN npm run build

# ------------------------------
# STAGE 2: Serve with Nginx
# ------------------------------
FROM nginx:1.27-alpine AS production-stage

# Copy built files from build stage
COPY --from=build-stage /app/dist /usr/share/nginx/html

# Copy a custom nginx.conf if you have one
# Uncomment and add your config if needed
# COPY nginx.conf /etc/nginx/conf.d/default.conf

# Expose the default Nginx port
EXPOSE 80

# Use a stable entrypoint
CMD ["nginx", "-g", "daemon off;"]
