FROM node
RUN mkdir -p /usr/src/app
WORKDIR /usr/src/app
COPY backend/package.json /usr/src/app
RUN npm install
COPY . .
EXPOSE 8000
EXPOSE 3306
CMD ["npm", "start"]
# COPY . /usr/src/app
