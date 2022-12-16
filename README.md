# Validated Patterns for Sepsis-Detection
    This project is the Validated patterns implementation for Original [Sepsis Dectection project](https://github.com/redhat-na-ssa/himss-2021-sepsis-gitops)It implements all the components as helm charts and charts are located under (charts/all/sepsis-demo)

## prerequisites

    1) OCP cluster version 4.11 (This is tested with OCP 4.11)

## installation
 
   ```
    git clone https://github.com/redhat-na-ssa/himss-2021-sepsis-gitops.git

    oc login --token=<<TokenValue>> --server=<<OCP API Cluster Server>

    make install
   ```

## Add New components to chart

   1) Checkout branch `my-branch`
   
   2) Create New Template :

   ``` 
    cd charts/all/sepsis-demo
    helm create <<ChartName>>
   ``` 

   3) Testing the template :

   ` helm template <<Chart Directory>> `

   4) Edit `values-datacenter.yaml` add the created chart under applications :

   5) Commit the changes and push the branch
       
        ```
            git add .
            git commit -m <<Message>>
            git push
        ```

   6) Update the Cluster

      ` make upgrade `         


## Reference Documentation for Multicloud Gitops can be found here


[Multicloud GitOps](http://hybrid-cloud-patterns.io/multicloud-gitops/)
for additional context and installation instructions

## Argo Dex server patch ()

    This command needs to be used if Argo fails to open.

oc patch deploy/datacenter-gitops-dex-server --type='json' -p='[{"op": "replace", "path": "/spec/template/spec/containers/0/securityContext/runAsNonRoot", "value": 'false'}]' -n himss-2021-sepsis-gitops-datacenter