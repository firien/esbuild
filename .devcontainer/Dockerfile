FROM node:16-alpine AS node

FROM golang:1.19.0-alpine3.16
# copy node & npm (i must be doing something wrong because this should be easier)
COPY --from=node /usr/local/bin/node /usr/local/bin/
RUN mkdir /usr/local/lib/node_modules
COPY --from=node /usr/local/lib/node_modules /usr/local/lib/node_modules/
# symlink npm & npx
RUN ln -s /usr/local/lib/node_modules/npm/bin/npm-cli.js /usr/local/bin/npm &&\
    ln -s /usr/local/lib/node_modules/npm/bin/npx-cli.js /usr/local/bin/npx

RUN apk update -qq && apk add --no-cache libstdc++ git make build-base

CMD ["sleep", "infinity"]
