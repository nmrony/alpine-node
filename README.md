Minimal NodeJS Docker Image
===========================
This image is built on **[Alpine Linux][1] Edge Version** to maintain small footprint

Available Versions
-------------------
1. Current Versions
   - `latest`, `v6.2.1` with `NPM` v3.9.5

Checking Versions
-----------------
To run container run the following command
```sh
$docker run --rm --name node_v nmrony/alpine-node node -v
#6.2.1
$docker run --rm --name npm_v nmrony/alpine-node npm -v
#3.9.5
```  
Running your App
-----------------
To run your App run the following command given below (You need to change the path and command to reflect your app path)
```sh
$cd /path/to/project/root
#install dependencies
$docker run --rm --name awesome_node_app_install -v $(pwd):/app -w /app nmrony/node-alpine npm i
#Running App
$docker run --name awesome_node_app -v $(pwd):/app -w -p 80:<your-app-port> /app nmrony/node-alpine node start-file.js

```

[1]: http://www.alpinelinux.org/
