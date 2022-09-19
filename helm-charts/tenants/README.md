# Helm Chart For OpenShift/Kubernetes Tenant Management

This helm chart created for a special requirement and replace the OpenShift default project template with this helm chart. 

## Sample Value File
Multi tenants can be created, each tenant can have multiple projects and projects can also have multiple namespaces.
Below commented section is a new tenant. 

Resource quotas and Limit ranges can be configured. 

```
tenants:
  - name: tenant-a
    project: 
      - name: project-alpha
        namespaces:
          - name: build
            admin: "someone@domain.com"
            resourceQuota:
              pods: 10
              cpuLimits: 6
              cpuRequests: 4
              memoryLimits: 16Gi
              memoryRequests: 8Gi
            limits:
              maxCpu: 4
              maxMemory: 2Gi
              minCpu: 10m
              minMemory: 128Mi
          - name: dev
            admin: "someone@domain.com"
            resourceQuota:
              pods: 20
              cpuLimits: 6
              cpuRequests: 4
              memoryLimits: 16Gi
              memoryRequests: 8Gi
            limits:
              maxCpu: 4
              maxMemory: 2Gi
              minCpu: 10m
              minMemory: 128Mi
          - name: stage
            admin: "someone@domain.com"
            resourceQuota:
              pods: 30
              cpuLimits: 6
              cpuRequests: 4
              memoryLimits: 16Gi
              memoryRequests: 8Gi
            limits:
              maxCpu: 4
              maxMemory: 2Gi
              minCpu: 10m
              minMemory: 128Mi
          - name: ppe
            admin: "someone@domain.com"
            resourceQuota:
              pods: 30
              cpuLimits: 6
              cpuRequests: 4
              memoryLimits: 16Gi
              memoryRequests: 8Gi
            limits:
              maxCpu: 4
              maxMemory: 2Gi
              minCpu: 10m
              minMemory: 128Mi
      - name: project-beta
        namespaces:
          - name: build
            admin: "someone@domain.com"
            resourceQuota:
              pods: 10
              cpuLimits: 6
              cpuRequests: 4
              memoryLimits: 16Gi
              memoryRequests: 8Gi
            limits:
              maxCpu: 4
              maxMemory: 2Gi
              minCpu: 10m
              minMemory: 128Mi
  # - name: tenant-b
  #   project: 
  #     - name: project-alpha
  #       namespaces:
  #         - name: build
  #           admin: "someone@domain.com"
  #           resourceQuota:
  #             pods: 10
  #             cpuLimits: 6
  #             cpuRequests: 4
  #             memoryLimits: 16Gi
  #             memoryRequests: 8Gi
  #           limits:
  #             maxCpu: 4
  #             maxMemory: 2Gi
  #             minCpu: 10m
  #             minMemory: 128Mi
```

# Installation 

To install the helm chart follow the below step

```
helm repo add arunalakmal https://arunalakmal.github.io/helm-repo
helm repo update
```

Create a custom value file named `custom-values.yaml` as per the requirement editing the above values file (This is the same default value file) and execute the below command 
```
helm install tenants arunalakmal/tenants -f custom-values.yaml
```
Check and confirm the helm release status 

```
helm list
```
