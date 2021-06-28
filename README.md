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

3. Once microservice is successfully deployed you should get a response that looks like this:
```
created: 1617907116
digest:  sha265:e38a0314ea4bca42802bbc315637d9db9251158494e85ece4c0d789e2ab0b191
id:      79279c04-8945-4141-8b52-2cb92b78cf43-microservice-v1
name:    microservice-v1
size:    75855
status:  successfully deployed
```

4. Navigate to where 'start-mDebug.json' is located and run command: 
```
mimik-edge-cli container deploy --payload start-mDebug.json --token={EDGE_ACCESS_TOKEN}
```

- For more information and explanation, you can visit our [mCM container management API references](https://developer.mimik.com/edgeengine-mcm-api/) and [general guide on packaging, deployment, and exporting microservice](https://developer.mimik.com/building-edge-microservices/).
