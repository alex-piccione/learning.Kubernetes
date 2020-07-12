# Start from a Node.js 10 (LTS) image
FROM node:10

# Specify the directory inside the image in wich all commands will run
WORKDIR /usr/src/app

# Copy package files and install dependency
COPY package*.json ./
RUN npm install

# Copy all the app files into the image
COPY . .

# The default command to run when starting the container
CMD ["npm", "start"]