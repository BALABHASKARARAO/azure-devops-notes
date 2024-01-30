## azure devop yaml strcutre


* https://learn.microsoft.com/en-us/azure/devops/pipelines/yaml-schema/?view=azure-pipelines


```
trigger:
- master
- develop
- feature/*

pool:
  vmImage: ubuntu-latest
```