FROM node:10.16-alpine

ARG SRCROOT=/usr/local/src/chainlink
WORKDIR ${SRCROOT}
COPY yarn.lock package.json tsconfig.cjs.json ./
COPY tools/echo-server/package.json tools/echo-server/

# install deps for our integration scripts
RUN yarn

# copy over all our dependencies
COPY tools/echo-server tools/echo-server

# setup project
RUN yarn workspace @chainlink/echo-server setup

ENV PORT 6690
EXPOSE 6690

ENTRYPOINT [ "yarn", "workspace", "@chainlink/echo-server", "start" ]
