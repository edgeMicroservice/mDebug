# mDebug
mDebug Utility/Debugging microservice. Deploy this microservice to view all the devices in your edge clusters

# Prerequisite
---
- You must have edgeEngine running and associated 
- You must have mimik-edge-cli tool [More info](https://www.npmjs.com/package/@mimik/mimik-edge-cli)
- Use cli tool to retrieve your EDGE_ACCESS_TOKEN. You will need it for deployment

# Deployment
---
1. Download the latest release here: [mDebug releases](https://github.com/edgeMicroservice/mDebug/releases)
2. Use mimik-edge-cli to deploy the microservice
```
mimik-edge-cli image deploy --image={YOUR_IMAGE_PATH} --token={EDGE_ACCESS_TOKEN}
```

3. Once microservice is successfully deployed you should get output that looks like this:
```
created:  1624894895
digest:   sha265:70b7f58854b9d79abfa653d7abcacb9a9e9225f38d731af718fc2eca6bf04a20
id:       79279c04-8945-4141-8b52-2cb92b78cf43-mdebug-v1
name:     mdebug-v1
repoTags:
  - mdebug-v1:1.1.0
size:     131910
status:   successfully deployed
```

4. Navigate to where 'start-mDebug.json' is located and run command: 
```
mimik-edge-cli container deploy --payload start-mDebug.json --token={EDGE_ACCESS_TOKEN}
```
5. After successful container initialization you will get output similar to below:
```
clientId: 79279c04-8945-4141-8b52-2cb92b78cf43
created:  1624895009469
env:
  MCM.BASE_API_PATH:                  /79279c04-8945-4141-8b52-2cb92b78cf43/mdebug-v1/v1
  MCM.DB_ENCRYPTION_SUPPORT:          false
  MCM.LINKLOCAL_REPLAY_NONCE_SUPPORT: false
  MCM.WEBSOCKET_SUPPORT:              false
  ownerCode:                          1234
id:       79279c04-8945-4141-8b52-2cb92b78cf43-mdebug-v1
image:    mdebug-v1
imageId:  79279c04-8945-4141-8b52-2cb92b78cf43-mdebug-v1
name:     mdebug-v1
state:    started
```

6. Use the value for your "MCM.BASE_API_PATH:" to get to the gui. All you need to do is copy the value for MCM.BASE_API_PATH and add "/gui" to the end of it. EX:
```
/79279c04-8945-4141-8b52-2cb92b78cf43/mdebug-v1/v1/gui
```
7. Call the gui endpoint from a browser of your choice. you will need the full URL. This will open the gui in the browser EX:
```
http://localhost:8083/79279c04-8945-4141-8b52-2cb92b78cf43/mdebug-v1/v1/gui
```

- For more information and explanation, you can visit our [mCM container management API references](https://developer.mimik.com/edgeengine-mcm-api/) and [general guide on packaging, deployment, and exporting microservice](https://developer.mimik.com/building-edge-microservices/).
