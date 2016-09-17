Minimal NodeJS Docker Image
===========================
This image is built on **[Alpine Linux][1] Edge Version** to maintain small footprint

Available Versions
-------------------
**Current Versions**
 1. `latest`, `6.2.2` with `NPM v3.10.2`
 1. `6.2.1` with `NPM v3.9.5`

**LTS Versions**
  1. `lts`, `4.5.0` with `NPM v2.15.11`  

> **Check Tags to find out available NodeJS version**

Checking Versions
-----------------
To run container run the following command
```sh
$docker run --rm --name node_v nmrony/alpine-node node -v
6.2.2
$docker run --rm --name npm_v nmrony/alpine-node npm -v
3.10.2
```
Using as Base Image
-------------------
If you want to use it as your base image you your `Dockerfile` should look like below
```sh
FROM nmrony/alpine-node
# FROM nmrony/alpine-node:6.2.2
# FROM nmrony/alpine-node:lts
# FROM nmrony/alpine-node:4.5.0

WORKDIR /app
ADD . .

# If you have to compile modules with node-gyp,
# you'll need extra tools. Uncomment the line below
# RUN apk add --no-cache make gcc g++ python

RUN npm install

# Replace app-port with your own one
EXPOSE [app-port]

# Replace app-entrypoint.js with your own one
CMD ["node", "app-entrypoint.js"]
```

Running your App
-----------------
To run your App run the following command given below (You need to change the path and command to reflect your app path)
```sh
$cd /path/to/project/root
#install dependencies
$docker run --rm --name awesome_node_app_install -v $(pwd):/app -w /app nmrony/alpine-node npm i
#Running App
$docker run --name awesome_node_app -v $(pwd):/app -w /app -p 80:<your-app-port> nmrony/alpine-node node [app-entrypoint.js]
```

[1]: http://www.alpinelinux.org/
