`creating a shell demo`

curl -o- [https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.3/install.sh](https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.3/install.sh) | bash
kubectl apply -f [https://k8s.io/examples/application/shell-demo.yaml](https://k8s.io/examples/application/shell-demo.yaml)
kubectl exec -it shell-demo -- /bin/bash

kubectl delete pod shell-demo

`fetching github repos`

gh repo list <owner|org> --limit 1000 | awk '{print $1;}' | xargs -L1 gh repo clone 

`debugging individual files`

1. add this in the beginning of the file you want to test

import dotenv from 'dotenv'
dotenv.config()

 2.  click on `Run and Debug` tab  
 3.  click on `create a launch.json file`  
 4. select `Node.js`  
 5. in the `launch.json` file, replace content with this:  

{
  "version": "0.2.0",
  "configurations": [
    {
      "name": "Current TS Tests File",
      "type": "node",
      "request": "launch",
      "program": "${workspaceRoot}/node_modules/mocha/bin/_mocha",
      "args": ["-r", "ts-node/register", "${relativeFile}"],
      "cwd": "${workspaceRoot}",
      "internalConsoleOptions": "openOnSessionStart"
    },
    {
      "name": "Current TS File",
      "type": "node",
      "request": "launch",
      "args": ["${relativeFile}"],
      "runtimeArgs": ["-r", "ts-node/register", "-r", "tsconfig-paths/register"],
      "cwd": "${workspaceRoot}",
      "env": [],
      "internalConsoleOptions": "openOnSessionStart"
    }
  ]
}

 6.  add breakpoint to the code you want to test  
 7. in the `Run and Debug` tab, select `Current Ts File` and hit the play button

 `mysql util command`

 ```
mysqlsh -- util checkForServerUpgrade host@ip
```


 
