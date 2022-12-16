# Start Here

If you've followed a link to this repo, but are not really sure what it contains
or how to use it, head over to [Multicloud GitOps](http://hybrid-cloud-patterns.io/multicloud-gitops/)
for additional context and installation instructions

## Argo Dex server patch
oc patch deploy/datacenter-gitops-dex-server --type='json' -p='[{"op": "replace", "path": "/spec/template/spec/containers/0/securityContext/runAsNonRoot", "value": 'false'}]' -n himss-2021-sepsis-gitops-datacenter