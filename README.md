## Halkyon.io web site

This web site is for the moment used to redirect incoming HTTP requests to reply with a `<meta content` tag

Information is available here:
- https://golang.org/cmd/go/#hdr-Remote_import_paths
- https://stackoverflow.com/questions/26347516/using-go-get-on-a-personal-git-repo

Command to be used to deploy and configure the `halkyon nginx server` is 

```
oc project halkyonio-site
oc apply -f resources/common.yml
```

If the project is deployed on openshift, install the route 
```bash
oc apply -f resources/route.yml
```
and the ingress resource for a k8s cluster
```bash
oc apply -f resources/ingress.yml
```

Check if we get a meta tag 
```bash
curl -sL https://halkyon.io/operator?go-get=1 | grep -i go-import
<html><head><meta name="go-import" content="halkyon.io/operator git git+ssh://git@github.com/halkyonio/operator"/></head></html>
```
an next if you can get the go project
```bash
go get -v halkyon.io/operator  
```

## NOT USED

For git+ssh project, use the following location return response
```bash
return 200 '<html><head><meta name="go-import" content="halkyon.io$1 git git+ssh://git@github.com/halkyonio$1"/></head></html>';
``` 