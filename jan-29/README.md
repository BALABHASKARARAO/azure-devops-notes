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

```
trigger:
- master
- develop
- feature/*

pool:
  vmImage: ubuntu-latest

steps:
- script: |
    echo "bala"
    echo "bhaskar"
```

* Build across multiple platforms
```
* https://learn.microsoft.com/en-us/azure/devops/pipelines/customize-pipeline?view=azure-devops

trigger:
- main

strategy:
  matrix:
    linux:
      imageName: "ubuntu-latest"
    mac:
      imageName: "macOS-latest"
    windows:
      imageName: "windows-latest"
  maxParallel: 1

pool:
  vmImage: $(imageName)


- script: 'dotnet --info'
  displayName: 'Command Line Script'
```