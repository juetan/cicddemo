FROM node:18-alpine As dev
WORKDIR /app
COPY package*.json .
RUN npm install
COPY . .
RUN npm run build && npm prune --production

FROM node:18-alpine As build
WORKDIR /app
ENV NODE_ENV production
COPY --from=dev /app/dist/ ./dist/
COPY --from=dev /app/node_modules/ ./node_modules/

EXPOSE 3000
CMD [ "node", "./dist/main.js" ]
