
#### 🚨 **Important NOTE:** 🚨
**This mDebug repository has been archived and is no longer maintained.**  
Please visit our new repository [mInsight](https://github.com/edgeMicroservice/mInsight) for the latest updates.

# mDebug
mDebug Utility/Debugging microservice. Deploy this microservice to view all the devices in your edge clusters

# Prerequisite
---
- You must register a mimik developer account on [developer console](https://developer.mimik.com/console/).
- You understands [edgeEngine Tokens](https://devdocs.mimik.com/key-concepts/03-index)
- You must have [mimik-edge-cli tool](https://devdocs.mimik.com/tutorials/03-index) ([More info](https://www.npmjs.com/package/@mimik/mimik-edge-cli))
- Use cli tool to retrieve your EDGE_ACCESS_TOKEN. You will need it for microservice deployment
```
mimik-edge-cli account get-edge-access-token -f .dev_id_token | jq -r .access_token > .access_token
```
- You must have edgeEngine running.
> **_NOTE:_** If the edgeEngine runtime is not on the localhost, you should setup 'EDGE_ENGINE_URI' environment variable.  For example, on Linux, you can do the following
```
EDGE_ENGINE_URI=172.168.0.1:8083 mimik-edge-cli account get-edge-access-token -f=.dev_id_token
```

# Deployment
---
1. Download the latest release here: [mDebug releases](https://github.com/edgeMicroservice/mDebug/releases)
2. Use mimik-edge-cli to deploy the microservice
```
mimik-edge-cli image deploy --image={YOUR_IMAGE_PATH} -f .access_token | jq
```

3. Once microservice image is successfully deployed, you should get output that looks like this:
```
{
  "created": 1681237042,
  "digest": "sha265:71a131b0de56eee342cc55fd6243f190d3c41ac9b5e2e37136fc71d4bfd87828",
  "id": "79279c04-8945-4141-8b52-2cb92b78cf43-mdebug-v1",
  "name": "mdebug-v1",
  "repoTags": [
    "mdebug-v1:1.2.0",
    "runtime:js"
  ],
  "size": 127012,
  "status": "successfully deployed"
}
```

4. Navigate to where 'start-mDebug.json' is located and run command: 
```
mimik-edge-cli container deploy --payload start-mDebug.json -f=.access_token | jq
```
5. After successful container initialization you will get output similar to below:
```
{
  "clientId": "79279c04-8945-4141-8b52-2cb92b78cf43",
  "created": 1681237900819,
  "env": {
    "MCM.BASE_API_PATH": "/79279c04-8945-4141-8b52-2cb92b78cf43/mdebug-v1/v1",
    "MCM.DB_ENCRYPTION_SUPPORT": "true",
    "MCM.LINKLOCAL_REPLAY_NONCE_SUPPORT": "false",
    "MCM.RUNTIME": "js",
    "MCM.WEBSOCKET_SUPPORT": "false",
    "ownerCode": "1234"
  },
  "id": "79279c04-8945-4141-8b52-2cb92b78cf43-mdebug-v1",
  "image": "mdebug-v1",
  "imageId": "79279c04-8945-4141-8b52-2cb92b78cf43-mdebug-v1",
  "name": "mdebug-v1",
  "state": "started"
}
```

6. Use the value for your "MCM.BASE_API_PATH:" to get to the gui. All you need to do is copy the value for MCM.BASE_API_PATH and add "/gui" to the end of it. EX:
```
/79279c04-8945-4141-8b52-2cb92b78cf43/mdebug-v1/v1/gui
```
7. Call the gui endpoint from a browser of your choice. you will need the full URL. This will open the gui in the browser EX:
```
http://{EDGE_ENGINE_IP}:8083/79279c04-8945-4141-8b52-2cb92b78cf43/mdebug-v1/v1/gui
```

- For more information and explanation, you can visit our [Getting Up and Running with mDebug](https://devdocs.mimik.com/tutorials/06-index)
