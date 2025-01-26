FROM node:22-slim

WORKDIR /app/ui

# Copy package.json and install dependencies
COPY ./sveltekit/package.json ./sveltekit/package-lock.json ./
RUN npm install

# Copy application code
COPY ./sveltekit/ .

# Expose the application port
EXPOSE 5173

# Run the SvelteKit application
ENTRYPOINT ["npm", "run", "dev"]
