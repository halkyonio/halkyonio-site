## Halkyon.io web site

This web site is for the moment used to redirect incoming HTTP requests to reply with a `<meta content` tag

Information is available here:
- https://golang.org/cmd/go/#hdr-Remote_import_paths
- https://stackoverflow.com/questions/26347516/using-go-get-on-a-personal-git-repo

Command to be used to deploy and configure the nginx server is 

```
oc project halkyonio-site
oc apply -f configmap.yml
oc apply -f service.yml
oc apply -f deployment.yml
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
