# Use an official base image with both Node and Python
FROM node:18-bullseye

# Install Python + pip
RUN apt-get update && apt-get install -y python3-pip

# Set working directory
WORKDIR /app

# Copy files
COPY . .

# Install Python deps
RUN pip3 install -r requirements.txt

# Install Node deps
RUN npm install

# Expose your app port (default 5000)
EXPOSE 5000

# Start the server
CMD ["npx", "tsx", "server/index.ts"]
