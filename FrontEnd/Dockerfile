FROM node
RUN mkdir -p /usr/src/app
WORKDIR /usr/src/app
COPY FrontEnd/package.json /usr/src/app
RUN npm install
COPY app.js .
EXPOSE 5000
CMD ["npm", "start"]
# COPY . /usr/src/app
