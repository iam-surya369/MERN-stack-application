#STAGE-1
#Base image
FROM node:22.7.0 AS builder

#Set the working directory
WORKDIR /app

#Copy the dependencies
COPY package*.json ./

#Install the dependencies
RUN npm install

#Copy the source code
COPY . .

#STAGE-2
#Copy the Stage-1
FROM node:22.7.0-slim AS production

#Set the working directory
WORKDIR /app

#Copy the files from the build stage
COPY --from=builder /app /app/

#Expose the port
EXPOSE 5050

#Default command to start the app
CMD [ "npm", "start" ]